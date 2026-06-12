---
title: "how to extract binay files?"
date: 2009-05-24
forum: General Help
---

### Post by sudoomar on 2009-05-24
hello

i have download a program compressed/splitted in 29 files i think
the files'extension is .bin

how can i extract/run these files

i tried the command bash but it says cannot execute binay file

thanx

---

### Post by mellowd on 2009-05-24
what file is it?

---

### Post by sudoomar on 2009-05-24
> **mellowd said:**
> what file is it?

i have 29 files 

in a directory /home/omar/Destkop/mtb

they are named MTB.RAR.01 ( with .bin extenion) to MTB.RAR.29

---

### Post by mellowd on 2009-05-24
open a terminal, change to the directory the files and in and type:

```
file MTB.RAR.01
```

Paste the result here. I'm not sure if these are rar files or what, but this command will help

---

### Post by sudoomar on 2009-05-24
> **mellowd said:**
> open a terminal, change to the directory the files and in and type:

```
file MTB.RAR.01
```

Paste the result here. I'm not sure if these are rar files or what, but this command will help

omar@omar-laptop:~/Desktop/mtb$ file MTB.RAR.01
MTB.RAR.01: RAR archive data, v1d, os: Unix
omar@omar-laptop:~/Desktop/mtb$ 

i used winrar with wine it says unexpected end of archive

the same errore when i used ./MTB.RAR.01

does that mean that simply the archive is corrupted?

---

### Post by mellowd on 2009-05-24
Could be. Could be that you're missing a file. Or it could just be that they are named incorrectly.

Try this:

```
sudo aptitude install unrar
```

Then go back to the folder with these files in and type:

```
unrar e MTB.RAR.01
```

Paste any errors you get over here

---

### Post by sudoomar on 2009-05-24
> **mellowd said:**
> Could be. Could be that you're missing a file. Or it could just be that they are named incorrectly.

Try this:

```
sudo aptitude install unrar
```

Then go back to the folder with these files in and type:

```
unrar e MTB.RAR.01
```

Paste any errors you get over here

Extracting  Mathworks Matlab R2007a UNIX.ISO                          99%
Encrypted file:  CRC failed in Matlab R2007a UNIX/Mathworks Matlab R2007a UNIX.ISO (password incorrect ?)
Unexpected end of archive

maybe i missed the password 
thankx very much

---

### Post by mellowd on 2009-05-24
Sounds like it, but it might alos be corrupt. Let me know how you get on

---

### Post by radi0j0hn on 2009-05-24
A lot of torrent files (especially movies) are broken into RAR files with each numbered consecutively.  With Ubuntu, you click on the first one and "extract here."  The program will jump to the next RAR file until all are extracted into one (or more) files ready for use.

If you are getting an "unexpected' end of files, it usually means that one of the RAR files is missing or corrupted.

---

### Post by sudoomar on 2009-05-24
Guys the files were split
i managed to merge them
i used HJsplit with wine
it is ok now

---

