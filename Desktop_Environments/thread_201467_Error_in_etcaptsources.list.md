---
title: "Error in /etc/apt/sources.list"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Ted D. on 2006-06-21
I am getting the following error messages.

In the update manager:
"This is a major failure of your software management system. Check file permisssion and correctness of the file /etc/apt/sources.list and relad the software apt-get update".
In the Synaptic package manager:
"E:Type 'wget' is not known on line 50 in source list.
E:The list of sources could not be read. Go to the repository dialog to correct the problem.

Tried going to the repository dialog (In Synaptic package manager) but could not find where to fix this probelm.
Assistance please and thanks in advance.
Ted D.

---

### Post by x64Jimbo on 2006-06-21
can you post your whole sources.lst file? I have the feeling I know what the problem is, but I can't tell you exactly how to correct it without referencing it in whole.

---

### Post by aysiu on 2006-06-21
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bad
gksudo gedit /etc/apt/sources.list
``` Delete line 50--the one with *wget* in it.

---

### Post by x64Jimbo on 2006-06-22
I wouldn't go suggesting deletion of an entire line... It's quite possible that the error is only in that one word. That's why I asked for a complete sources.lst file so we could examine in context.

---

### Post by Ted D. on 2006-06-22
[QUOTE=x64Jimbo]I wouldn't go suggesting deletion of an entire line... It's quite possible that the error is only in that one word. That's why I asked for a complete sources.lst file so we could examine in context.[/QUOTE]


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

# deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
# deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

# deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


# deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
## created by arnielistenadded

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)

Looking at this line I think it ok to delete it all.
Recommendations? Thanks

---

### Post by Ted D. on 2006-06-22
[QUOTE=x64Jimbo]I wouldn't go suggesting deletion of an entire line... It's quite possible that the error is only in that one word. That's why I asked for a complete sources.lst file so we could examine in context.[/QUOTE]



Correction. I mean delete the whole of the last line.[/COLOR]

---

### Post by x64Jimbo on 2006-06-22
Yes, it is OK to delete that very last line in its entirety. 
I think someone's tutorial around here must be confusing because you're the second person today who has had a linux command line parameter in his/her sources.lst file. It probably doesn't make a lot of sense, but I'll try to put it simply:
sources.lst is a very general reference point that the Aptitude program references in order to figure out where it can go to find packages.
Any time someone tells you to type a command like wget <parameter> or apt-get install <parameter> you should be typing it at the prompt like you would in DOS:
$ sudo apt-get install foo
$ wget [http://www.bar.com/foo.jpg](http://www.bar.com/foo.jpg)
Make sense?

---

### Post by Ted D. on 2006-06-22
Thanks. 
I think it was my error not the tutorial. Still learning

---

