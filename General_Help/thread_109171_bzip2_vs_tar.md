---
title: "bzip2 vs tar"
date: 2005-12-28
forum: General Help
---

### Post by Masteroc on 2005-12-28
Just wondering which compression method is the best for backups and file archiving. Does anyone have a link to a good comparison?

Thanks

---

### Post by amohanty on 2005-12-28
Just to clear some misconception lots of people have - "tar is _not_ a compression program" - it merely puts a bunch of file together and allows you some fancy backup options like incremental bkups, differential backups, checkpoints etc. The name comes from '**T**ape **Ar**chiv<something>'. 

bzip is an actual compression algorithm, tar provides gateways to using the gzip and bzip2 utilities via a single command line. Typically what you would want to do is to tar and gzip/bzip2 a bunch of files or folders and copy them over to media - simple usage:

gzip compression:
tar -c**z**f xyz.tar.gz <folder name>

bzip2 compression
tar -c**j**f xyz.tar.bz2 <folder name>

I would suggest going through the tar [manual]("http://www.gnu.org/software/tar/manual/html_mono/tar.html")
to get feel for what it can do.

HTH
AM

---

### Post by Masteroc on 2005-12-28
Sry for the misconception.

And thanks for the response

---

### Post by Rinzwind on 2005-12-28
He's correct. On Unix after tar'ing a file you **compress** it to shrink it.

And bzip2 is excellent :) It saves me hours of waiting when I need to throw some 100 Mb in software and date-files over to install it :)

---

