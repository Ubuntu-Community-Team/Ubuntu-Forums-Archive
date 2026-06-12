---
title: "Anyone setup a BLAST server?"
date: 2007-02-09
forum: Education &amp; Science
---

### Post by Rohan on 2007-02-09
Hi I'm looking to setup a wwwblast server for my lab and was just curious if anyone has got one running. 

I was just looking for tips and some help with picking out the hardware.

---

### Post by slaanco on 2007-02-11
what r the difference between apache and Blast ?

---

### Post by Rohan on 2007-02-11
Well APACHE is a http server that's really easy to setup. Especially in a debian OS that has a package already ready to go. 

BLAST searches pretty big databases and is pretty hardware intensive. You have to build the package yourself and get the databases from the NCBI and format them correctly for the BLAST server to be of any use. I have a feeling that keeping the databases up to date even with their script won't be that trivial.

---

### Post by kOoLiNuS on 2007-04-26
Uhm .... i am setting up a little wwwblast server to run on an HP Proliant DL140 (not sure about the model name) only with "my" genomics database.

The **wwwblast** package itself comes precompiled and "ready" to run: [http://130.14.29.110/BLAST/download.shtml](http://130.14.29.110/BLAST/download.shtml)

{probably you will already know about it}

For what regards the best hardware configuration I suppose it's all about the kind of service you're going to set up. In my case I have a 30 users maximum on a single genome type, so I think that my 2GB of RAM and on the dual Xeon will be enough ...


PS = in my Institute we also have an "old" Blast server installed on two (old) Digital UX machines, but the person responsible for it isn't present this week so I'll ask him ASAP !

---

### Post by Rohan on 2007-04-30
I don't think actually getting it running will be a problem (I was thinking of clustering at first but I don't really have enough computers). Anyways I decided on a Core 2 Quad. 

I guess the main issue is how to get keep the databases updated. Would it be possible to write a script? I'm fairly certain my lab uses the common databases on the NCBI site, do I still need to format the databases? Also, if a query is running and I have setup a script to update the databases will bad things happen if both try to run at the same time?

---

### Post by Dewni on 2008-01-08
I have recently set up a BLAST server in our department. 2, in fact, one on the server (Pentium 4Duo 3Ghz with 2Gb memory) and one on my dev machine (Intel Core2Duo @ 1.86 Ghz with 2Gb of memory)

I downloaded the current software (blast 2.2.17) from NCBI [ftp://ftp.ncbi.nlm.nih.gov/blast/executables/LATEST/blast-2.2.17-ia32-linux.tar.gz]("ftp://ftp.ncbi.nlm.nih.gov/blast/executables/LATEST/blast-2.2.17-ia32-linux.tar.gz")

and untarred it.

You can now run 

```
blastall -p blastn -d YOUR DATABASE -i INPUTFILE -o OUTPUTFILE
```
where the inputfile is a FASTA formatted file, the outputfile is much the same as you would get using the webpage at NCBI. The trick is, that your still need to build your database, which is some 2.5Gb worth of downloading for the mouse genome.

Since we were interested in mouse BLASTS, I build the mouse database:

First get the fasta data for all chromosomes from 
```
ftp://ftp://ftp.ncbi.nih.gov/genomes/M_musculus/Assembled_chromosomes/mm_ref_chrCHROMSOME NUMBER.fa.gz
```

Unpack those files with gunzip

Put everything in one file:
```

cat EACH FILE >> MouseNCBI36.fa
``` (build number 36 at  that time)

and create the database:

```
formatdb -t MouseNCBI36 -i MouseNCBI36.fa -l MouseNCBI36.log -pF -oT -n MouseNCBI36 -v 400 -V
```

After this you should be able to use blastall with the -d MouseNCBI36 option. 

If you are going to keep some older db builds it is probably wise to keep all these files somedisk spacious. The blastall program is looking for the database location in a .ncbirc file in your home directory. Below is mine:

```
[NCBI]
Data=/home/mhb/blast

[BLAST]
BLASTDB=/data_ex/blast/db

```

And, since I really can't be bothered remembering doing this in the right order, I put it in a bash script:
```
#! /bin/bash

# Download the current assembly from NCBI, when changed

echo "Build version in README_CURRENT_BUILD"
wget -N "ftp://ftp.ncbi.nih.gov/genomes/M_musculus/README_CURRENT_BUILD"
cat README_CURRENT_BUILD | grep "NCBI Build Number"


echo "Downloading files..."
for chrom in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 X Y
do
	time wget -N ftp://ftp.ncbi.nih.gov/genomes/M_musculus/Assembled_chromosomes/mm_ref_chr$chrom.fa.gz
done


echo "Extracting files..."
for chrom in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 X Y
do
	time gunzip mm_ref_chr$chrom.fa.gz
done

echo "Appending files..."

for chrom in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 X Y
do
	echo "...mm_ref_chr$chrom.fa"	
	cat mm_ref_chr$chrom.fa >>MouseNCBI37.fa
done


echo "Building BLAST databases (formatdb)"
	time  formatdb -t MouseNCBI37 -i MouseNCBI37.fa -l mouseNCBI37.log -pF -oT -nMouseNCBI37 -v 400 -V
```

Be carefull that building a DB  this way gives you coordinates relative to the contigs, so gene annotation of you BLAST hits requires you to get the corresponding data from ```
ftp://ftp.ncbi.nih.gov/genomes/M_musculus/mapview/seq_gene.md.gz
```

which you can just 
```
zcat seq_gene.md.gz > SOMEFILE.txt
```
to get to that set of coordinates.

I am betting that there is an easier way to get to those gene coordinates, but that data at least gives you exactly the same information as the NCBI mapview tool gives you, again relative to contig instead of chromosome.

Hope this helps.

---

### Post by ywurm on 2011-02-08
[Check this new blast server]("http://www.sequenceserver.com")

---

