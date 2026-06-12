---
title: "Backup my system"
date: 2009-03-15
forum: General Help
---

### Post by theozzlives on 2009-03-15
I want to create a *.tar.gz  backup using this [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")  but I want it to span CDs, or at least  make files in 300 MB chunks so I can burn it to CD. Is that possible?

---

### Post by dusan.saiko on 2009-03-16
yes, there is a split command you can use.
see "man split"

fo example:
tar cz * | split -d -a 4 -b 1000000 - archive.tgz.

will tar and compress everything (not hidden) in current directory and split it with
-d numeric sufixess
-a sufix lenght is 4
-b part size is 1 000 000 b (~1MB)
-  from standard input
archive.tgz. - prefix

this will create something like

-rw-r--r--  1 dsaiko dsaiko 1000000 2009-03-16 15:34 archive.tgz.0000
-rw-r--r--  1 dsaiko dsaiko  978527 2009-03-16 15:34 archive.tgz.0001


to unpack such archive use

cat archive.tgz.* | tar xvz

:-)

---

### Post by theozzlives on 2009-03-16
Thanks for the help (actually  a MB is 10240 bytes)

---

