---
title: "Dependency error installing .deb package"
date: 2009-05-20
forum: General Help
---

### Post by 45acp on 2009-05-20
I am trying to install a .deb package with the package manager. It gives a dependency error saying libgtk2.0-0 is not satisfied. Libgtk2.0-0 is installed. I even tried reinstalling it. Still I get the same error. Any ideas?

---

### Post by mb_webguy on 2009-05-20
What package are you trying to install?  Also, are you running 32-bit or 64-bit Ubuntu?

---

### Post by quincyicq on 2009-05-22
I'm having trouble with this issue as well.


I'm trying to update **devede v3.6** to the latest release **(3.13)** and after I try to install the .deb i get the following:


:/home/computer# dpkg --install devede_3.13.0-0~rastersoft1_all.deb 
Selecting previously deselected package devede.
(Reading database ... 131085 files and directories currently installed.)
Unpacking devede (from devede_3.13.0-0~rastersoft1_all.deb) ...
dpkg: dependency problems prevent configuration of devede:
 [B]devede depends on libgtk2.0-0 (>= 2.16.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.[/B]
dpkg: error processing devede (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 devede

Synaptic doesn't list anything above 2.12.9.

Software sources/repos are all enabled and to my knowledge up to date.
using hardy 8.04 Linux version 2.6.24-19-generic  (32bit)

Where/how would I obtain libgtk2.0-0 2.16+?


What version of libgtk is on the latest ubuntu release?

---

### Post by bacardiandwatermelon on 2009-05-22
Jaunty has libgtk2.0-0 v2.16.1-0ubuntu2

---

### Post by etnlIcarus on 2009-05-22
> **45acp said:**
> I am trying to install a .deb package with the package manager. It gives a dependency error saying libgtk2.0-0 is not satisfied. Libgtk2.0-0 is installed. I even tried reinstalling it. Still I get the same error. Any ideas?No one is going to be able to help you unless you tell us what you're trying to install, where you got it from and what version of Ubuntu you're running.

---

### Post by 45acp on 2009-05-22
I was trying to install fotoxx from getdeb. I also tried form the terminal. the error message said I need a higher version of libgtk2.0-0 than what is in the intrepid repros. I'll try later when I get home to snag a higher version. Thanks for th replies.

---

### Post by etnlIcarus on 2009-05-22
> **45acp said:**
> I was trying to install fotoxx from getdeb. I also tried form the terminal. the error message said I need a higher version of libgtk2.0-0 than what is in the intrepid repros. I'll try later when I get home to snag a higher version. Thanks for th replies.

[http://www.getdeb.net/distro_select.php](http://www.getdeb.net/distro_select.php)

Make sure you're downloading for the right distro.

---

