---
title: "Fluxbox Broken Styles"
date: 2005-10-28
forum: Desktop Environments
---

### Post by jtxx000 on 2005-10-28
I installed fluxbox according to the directions [here](http://www.ubuntuforums.org/showthread.php?t=35388&highlight=fluxbox), but there are no styles in the fluxbox menu despite the fact that the /usr/local/share/fluxbox/styles directory is full.

--Caleb

---

### Post by Riverside on 2005-10-29
[QUOTE=jtxx000]I installed fluxbox according to the directions [here](http://www.ubuntuforums.org/showthread.php?t=35388&highlight=fluxbox), but there are no styles in the fluxbox menu despite the fact that the /usr/local/share/fluxbox/styles directory is full.[/QUOTE]Fluxbox is a Blackbox derivative.  I have very little experience of Fluxbox, but a lot more with Blackbox.  At  a guess, your Fluxbox menu file doesn't know where the styles are located (if you even have a Fluxbox menu file, the Ubuntu packaged version of Blackbox doesn't have one, so it is quite likely that the Ubuntu packaged Fluxbox similarly doesn't).

You should have, apparently, a utility entitled fluxbox-generate_menu designed to generate a menu file automagically.  It might be worth running that and seeing how you get on.

---

### Post by Riverside on 2005-10-29
I just tried to install Fluxbox on Breezy in an attempt to assist further, however installation failed.  This may be because Blackbox is already installed, and the error message provided indicates that the Fluxbox package attempts to overwrite a file which is also installed by the Blackbox package:

> anthony@trafford:~$ sudo apt-get install fluxbox
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  menu
Suggested packages:
  fluxconf fbpager fbdesk xfonts-artwiz
The following NEW packages will be installed:
  fluxbox menu
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1162kB of archives.
After unpacking 4407kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe menu 2.1.25 [387kB]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe fluxbox 0.9.12-1build1 [775kB]
Fetched 1162kB in 19s (60.3kB/s)                                               

Preconfiguring packages ...
Selecting previously deselected package menu.
(Reading database ... 61783 files and directories currently installed.)
Unpacking menu (from .../archives/menu_2.1.25_i386.deb) ...
Selecting previously deselected package fluxbox.
Unpacking fluxbox (from .../fluxbox_0.9.12-1build1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/fluxbox_0.9.12-1build1_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/bsetroot.1.gz', which is also in package blackbox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/fluxbox_0.9.12-1build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Riverside on 2005-10-29
A known issue it seems:

[https://launchpad.net/distros/ubuntu/+source/blackbox/+bug/897](https://launchpad.net/distros/ubuntu/+source/blackbox/+bug/897)

---

### Post by jtxx000 on 2005-10-29
[QUOTE=Riverside]Fluxbox is a Blackbox derivative.  I have very little experience of Fluxbox, but a lot more with Blackbox.  At  a guess, your Fluxbox menu file doesn't know where the styles are located (if you even have a Fluxbox menu file, the Ubuntu packaged version of Blackbox doesn't have one, so it is quite likely that the Ubuntu packaged Fluxbox similarly doesn't).

You should have, apparently, a utility entitled fluxbox-generate_menu designed to generate a menu file automagically.  It might be worth running that and seeing how you get on.[/QUOTE]

Thanks, that did it. :)

---

