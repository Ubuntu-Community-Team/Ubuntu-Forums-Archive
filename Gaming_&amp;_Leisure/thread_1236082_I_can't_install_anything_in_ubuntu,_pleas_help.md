---
title: "I can't install anything in ubuntu, pleas help"
date: 2009-08-09
forum: Gaming &amp; Leisure
---

### Post by ydoc1992 on 2009-08-09
every time i try to install something i get an error.

cody@Mac:~$ sudo apt-get install egoboo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  egoboo-data
The following NEW packages will be installed:
  egoboo egoboo-data
0 upgraded, 2 newly installed, 0 to remove and 41 not upgraded.
Need to get 0B/15.8MB of archives.
After this operation, 40.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package egoboo-data.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `stoneredition-theme-pack-2.0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
cody@Mac:~$ 

this is my error please help me fix it and when i tryed to remove the theme pack it would not let me so if that is the problem how do i remove it.

---

### Post by ydoc1992 on 2009-08-09
i know i probably put this in the wrong place but im trying to install a few games egoboo and nethack

---

### Post by Grishka on 2009-08-09
try removing the "stoneredition-theme-pack-2.0" package.

edit: man, don't double post. try fixing the packages in synaptic.

---

