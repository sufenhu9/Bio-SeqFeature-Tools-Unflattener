# Bio-SeqFeature-Tools-Unflattener
The use_magic option in Bio::SeqFeature::Tools::Unflattener does not create correct structure for pseudogene

using Bio::SeqFeature::Tools::Unflattener to convert GenBank flat-feature-list to containment hierarchy shown below, Where each feature
is nested underneath its container.

From
gene
CDS

to
gene
 mRNA
  exon
  CDS

Everything is fine except the gene has pseudo tag when I use
$unflattener->unflatten_seq(-seq=>$seq, -use_magic=>1);

The gene has pseudo tag has been convert to pseudogene and pseudoCDS, and
they are flat. That is means pseudoCDS is not the children of pseudogene.

Like to know if there is any other parameter, or any other method that I
can use to convert both gene and pseudogene correctly.

Here is an example genbank file that has pseudogene tag (eg. NCLIV_066150).
http://www.ncbi.nlm.nih.gov/nuccore/FR823393

I am using bioperl_live/1.6.9,
$ perl -MBio::Root::Version -e 'print $Bio::Root::Version::VERSION,"\n"'
1.0069
