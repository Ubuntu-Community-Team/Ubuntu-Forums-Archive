---
title: "Problem with wget on symlinks."
date: 2009-01-25
forum: General Help
---

### Post by Yumyai on 2009-01-25
Hi,

I tried to use wget to recursively download some file on ftp, but it seems to have trouble with symlink folder.

First, I tried to use this command.

wget -r -N [ftp://ftp.ncbi.nih.gov/snp/database/organism_schema](ftp://ftp.ncbi.nih.gov/snp/database/organism_schema)   

( folders under organism_schema are symlink)

the problem is this command didn't download the file in folder, just download the symlink of folder and end there.

I tried to use --retr-symlinks options but it seems to  have error
```

--2009-01-25 13:24:14--  ftp://ftp.ncbi.nih.gov/snp/database/organism_data/arabidopsis_3702
           => `ftp.ncbi.nih.gov/snp/database/organism_data/arabidopsis_3702'
==> CWD not required.
==> PASV ... done.    ==> RETR arabidopsis_3702 ... 
No such file `arabidopsis_3702'.

--2009-01-25 13:24:15--  ftp://ftp.ncbi.nih.gov/snp/database/organism_data/bee_7460
           => `ftp.ncbi.nih.gov/snp/database/organism_data/bee_7460'
==> CWD not required.
==> PASV ... done.    ==> RETR bee_7460 ... 
No such file `bee_7460'.

--2009-01-25 13:24:16--  ftp://ftp.ncbi.nih.gov/snp/database/organism_data/bison_9901
           => `ftp.ncbi.nih.gov/snp/database/organism_data/bison_9901'
==> CWD not required.
==> PASV ... done.    ==> RETR bison_9901 ... 
No such file `bison_9901'.

```
and the list go on..

It's just bug or I use the wrong option ?. Thanks in advance !.

---

### Post by dcstar on 2009-01-25
> **Yumyai said:**
> Hi,

I tried to use wget to recursively download some file on ftp, but it seems to have trouble with symlink folder.

First, I tried to use this command.

wget -r -N [ftp://ftp.ncbi.nih.gov/snp/database/organism_schema](ftp://ftp.ncbi.nih.gov/snp/database/organism_schema)   

( folders under organism_schema are symlink)

the problem is this command didn't download the file in folder, just download the symlink of folder and end there.

I tried to use --retr-symlinks options but it seems to  have error
.........

Which is exactly how the wget man page says it works, it doesn't follow directory symlinks.

---

### Post by Yumyai on 2009-01-25
> **dcstar said:**
> Which is exactly how the wget man page says it works, it doesn't follow directory symlinks.

So, I can't use wget for this job right ? I'm using filezilla now, but I'm still curious that could I do all that thing in commandline.

---

### Post by jimv on 2009-01-25
Hold on...how does WGET know that a directory on a http server is a symlink?

---

