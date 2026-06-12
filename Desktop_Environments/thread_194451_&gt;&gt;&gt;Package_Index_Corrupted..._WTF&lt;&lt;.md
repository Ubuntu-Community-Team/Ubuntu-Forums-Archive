---
title: "&gt;&gt;&gt;Package Index Corrupted... WTF?&lt;&lt;&lt;"
date: 2006-06-11
forum: Desktop Environments
---

### Post by kickstar on 2006-06-11
hello,

when i do apt-get upgrade, it shows iv got 7 updates but they wont install because...

melluish@Ubuntu-Linux:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  acroread fb-music-high flashplugin-nonfree mplayer-fonts mplayer-skins
  msttcorefonts rar
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: The package index files are corrupted. No Filename: field for package acroread.

one thing that i did think of was that the updates are for packages that i installed via Automatix - and iv since removed it..

Any thoughts?

thanx!

---

### Post by tchock on 2006-06-11
Have you tried doing a 'sudo apt-get update'?

---

### Post by olddwarf on 2006-08-08
I had the same problem. Couln't install acroread nor GnomeBaker. Deleted all the 'gb.' from the source.list and did a apt-get update. Now I can install the apps and even get more written information in the application installer.
I looks as if there is a problem with the Ubuntu UK mirror.
Hope this is of help.

---

