---
title: "Need help finding how to on making deb packages"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Omnios on 2005-10-23
The other day I read a post on how to make a Deb package from scratch as I want to try it out on Gnome Sensors app which I downloaded mostly to have it show in synaptic so I can uninstall it when a new version comes out. I just spend an hour doing forum searches and notta thing to find. I think it was a horay post and the old release search seems to be BORKED. Anyone know its warabouts. I plan on Deb-ing every thing I download as having the ability to uninstall something is one of the reasons I am reluctent to download and install stuff not in synaptic.

---

### Post by GeneralZod on 2005-10-23
Do you mean creating a proper .deb with all the correct metadata and dependency lists etc, or just a .deb that has none of these things but can easily and correctly be installed/ uninstalled via dpkg? If the latter, you just need "checkinstall".

Edit:

Completely random link on the topic :)

[http://ubuntuforums.org/showthread.php?t=79841&highlight=checkinstall](http://ubuntuforums.org/showthread.php?t=79841&highlight=checkinstall)

---

### Post by Dr. Nick on 2005-10-23
Yeah checkinstall is what you want, install it via synaptic. Then download the source (.tar.gz) of the app you want to deb and do the "./configure" than "make" but instead of make install use sudo checkinstall and a .deb will be built. At the end it will let you change architecture type and type a description then it will instal the deb

---

### Post by Kyral on 2005-10-23
If you really wanna learn how to make Debpacks the proper way, the best source is the Debian New Maintainers Guide

[http://www.debian.org/doc/manuals/maint-guide/index.en.html](http://www.debian.org/doc/manuals/maint-guide/index.en.html)

And its in Debian Sid right now if you wanna go for it. Not saying its gonna work fully though ;P

[http://packages.debian.org/unstable/gnome/sensors-applet](http://packages.debian.org/unstable/gnome/sensors-applet)

---

