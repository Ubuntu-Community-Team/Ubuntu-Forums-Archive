---
title: "Configure nautilus-actions for command cat"
date: 2010-01-03
forum: Desktop Environments
---

### Post by Valeryan_24 on 2010-01-03
Hello,

I'm trying to join splitted files, types xxx.001 ... just 001, without xtm for example.

cat does it very well in command line (terminal):
cat *.xxx.* > file.avi

I'd like to configure Nautilus-actions to execute "cat" directly from explorer by selecting file 001, or all files to join, or the directory where there are, but I do not succeed.

In section "Command":
Path : I put "cat"
Parameters : my problem is here, I tried combinations %M , %d , %s , %f (ex: %d/%f > %d/Video.avi) but nothing works.

For shred, command is:
Path : shred
Parameters : -n 35 -z -u %M

To join pdf documents with pdftk :
Path : /usr/bin/pdftk
Parameters : %M cat output %d/fusion.pdf

And the GUI tools, like TuXtremsplit or Gnome-Split allow to concatenate 001.xtm files but not just 001...

Thanks in advance is someone has the solution (it's not a big problem, doing it via command line is well, but I'd like to find). :)

---

### Post by SalahTr on 2010-01-03
Hi Valeryan_24,

1-Put the attached script in :
```
 ~/.gnome2/nautilus-scripts/
```
2- Select files or directory containing files to join 
3-```
Right Click -> Scripts -> join_files.sh
```
4- Enter the destination file

---

### Post by Valeryan_24 on 2010-01-04
Thanks SalahTr,

It works very fine !

Also, coincidence, today the program Gnome Split has been updated and is now able to join xxx.001 files:

[https://www.ohloh.net/p/gnomesplit](https://www.ohloh.net/p/gnomesplit)

\\:D/

---

### Post by SalahTr on 2010-01-05
you're welcome

---

