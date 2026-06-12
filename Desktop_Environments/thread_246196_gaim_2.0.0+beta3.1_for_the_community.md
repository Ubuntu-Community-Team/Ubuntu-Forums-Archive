---
title: "gaim 2.0.0+beta3.1 for the community"
date: 2006-08-28
forum: Desktop Environments
---

### Post by lisa-m on 2006-08-28
i have built from source gaim 2.0 beta 3.1 on dapper drake, and i tested it and it worked like a charm on my computer and seemed fast and stable. So i decided to share my work with the rest fo the community. My first ever built package so enjoy it and i hope it works as good for everyone. Download the first two files and then from terminal go into folder where you have downloaded the files and type:

sudo dpkg -i gaim_2.0.0+beta3.1-1ubuntu2_i386.deb gaim-data_2.0.0+beta3.1-1ubuntu2_all.deb

you may install the other two packages if you wish, one is the debugger package and the other is a dev package which i'd recommend if you want to build any plugins e.t.c for you gaim.

links for package:
gaim_2.0.0+beta3.1-1ubuntu2_i386.deb [http://www.filefactory.com/file/bcb62d/]("http://www.filefactory.com/file/bcb62d/")
gaim-data_2.0.0+beta3.1-1ubuntu2_all.deb [http://www.filefactory.com/file/98c954/]("http://www.filefactory.com/file/98c954/")
gaim-dev_2.0.0+beta3.1-1ubuntu2_i386.deb [http://www.filefactory.com/file/8d0e5b/]("http://www.filefactory.com/file/8d0e5b/")
gaim-dbg_2.0.0+beta3.1-1ubuntu2_i386.deb [http://www.filefactory.com/file/6830b4/]("http://www.filefactory.com/file/6830b4/")

---

### Post by lisa-m on 2006-08-28
anyone try it, just want to know it works good? since it is my first built package and of a very essential piece of software.

---

### Post by lisa-m on 2006-08-29
bump

---

### Post by lisa-m on 2006-08-29
bump times 2... anyone try it?

---

### Post by Roasted on 2006-08-30
jason@jason-desktop:~$ sudo dpkg -i gaim_2.0.0+beta3.1-1ubuntu2_i386.deb gaim-data_2.0.0+beta3.1-1ubuntu2_all.deb
Password:
dpkg: error processing gaim_2.0.0+beta3.1-1ubuntu2_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing gaim-data_2.0.0+beta3.1-1ubuntu2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gaim_2.0.0+beta3.1-1ubuntu2_i386.deb
 gaim-data_2.0.0+beta3.1-1ubuntu2_all.deb
jason@jason-desktop:~$
jason@jason-desktop:~$





:confused: :confused: :confused: :confused: :confused:

---

### Post by phido on 2006-08-30
I've intalled gaim 2.0beta3 from here over Synaptic 
Add this to your sources.list and upgrade gaim
[I]deb [http://theli.free.fr/packages](http://theli.free.fr/packages) dapper theli
[/I]Worked well here.

Or you can download the packages
[http://theli.free.fr/packages/pool/theli/g/gaim/](http://theli.free.fr/packages/pool/theli/g/gaim/)
8)

---

### Post by Uncle Spellbinder on 2006-08-30
> **phido said:**
> I've intalled gaim 2.0beta3 from here over Synaptic 
Add this to your sources.list and upgrade gaim
[I]deb [http://theli.free.fr/packages](http://theli.free.fr/packages) dapper theli
[/I]Worked well here.

Or you can download the packages
[http://theli.free.fr/packages/pool/theli/g/gaim/](http://theli.free.fr/packages/pool/theli/g/gaim/)
8)

Same here, but mine came from this repo:

```
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
```

---

