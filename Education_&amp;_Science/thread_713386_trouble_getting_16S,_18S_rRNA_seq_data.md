---
title: "trouble getting 16S, 18S rRNA seq data"
date: 2008-03-02
forum: Education &amp; Science
---

### Post by querent on 2008-03-02
this isn't exactly an ubuntu question, but i thought i'd see what i come up with.

I'm a math-bio student with a soon-do, much-neglected project to worry about.  Basically its recreating the Pace et all tree (PMID: 9115194) with 150 rRNA sequences, 50 from each domain of life.  i'm to use muscle and mafft for the alignment (2 alignments) and mrbayes and raxml for the tree building (total: 4 trees).  I know I need one fasta format file to run muscle on.  how/where do I get the sequences and how to have them formatted properly.  I'm looking here for where to get the raw data, rather than info on each program.

thanks for any help.

---

### Post by DrOlaf on 2008-03-02
There are plenty of places from which you can download 16S or 18S RNA sequence data, but I don't know if you can get a pre-prepared version of the data used in Pace's article. The NCBI site [http://www.ncbi.nlm.nih.gov/]("http://www.ncbi.nlm.nih.gov/") has every sequence file ever produced in it, and you can just search it for the ones you want, but that would be very time-consuming. There are some databases with a narrower focus that may be useful to you, like the SILVA project database [http://www.arb-silva.de/](http://www.arb-silva.de/), that may be worth checking out. 

I see that you're in Boulder. That's where Norm Pace's lab is now located [http://pacelab.colorado.edu/index.html](http://pacelab.colorado.edu/index.html). You could always ask someone there - unless it's them who have set you this project :)

---

### Post by machoo02 on 2008-03-02
Just get them from Genbank.  Search for your specific gene and domain (something like "16s rRNA AND Domain[organism]" replacing Domain with your chosen domain of life), select the ones you want and copy them to the NCBI clipboard.  When you're all done, open up the clipboard, and choose "Fasta" from the output format, and export them to file.

---

### Post by querent on 2008-03-04
many thanks and good karma from the god of newbies.

q

---

