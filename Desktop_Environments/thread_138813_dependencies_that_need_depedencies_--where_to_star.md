---
title: "dependencies that need depedencies --where to start"
date: 2006-03-02
forum: Desktop Environments
---

### Post by lex1 on 2006-03-02
I have installed the bb 5-10 

where to start which is the file that does not need a dpenedcy?

 I tried apt-get -f install (but install what



You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  libwww-perl: Depends: liburi-perl (>= 1.10) but it is not going to be installed
               Depends: libhtml-parser-perl (>= 3.33) but it is not going to be installed
               Depends: libhtml-tree-perl (>= 3.11) but it is not going to be installed
  mixmaster: Depends: libmailtools-perl but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).


many thanks

lex:???: :???:

---

### Post by Xian on 2006-03-02
[QUOTE=lex1]I tried apt-get -f install (but install what[/QUOTE]

Go ahead and post the output of that command.
$ sudo apt-get -f install

---

### Post by Mr. Miner on 2007-05-18
Can you help me with this?  I'm trying to install kdenlive.

```
croberts@NEFERTITI:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mlt
The following NEW packages will be installed:
  mlt
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
Need to get 0B/3335kB of archives.
After unpacking 7975kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mlt
Install these packages without verification [y/N]? y
(Reading database ... 112000 files and directories currently installed.)
Unpacking mlt (from .../mlt_0.2.1-1+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mlt_0.2.1-1+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmlt.so.0.2.2', which is also in package libmlt0.2.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mlt_0.2.1-1+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by aysiu on 2007-05-18
Maybe try ```
sudo rm /usr/lib/libmlt.so.0.2.2
sudo apt-get -f install
```

---

