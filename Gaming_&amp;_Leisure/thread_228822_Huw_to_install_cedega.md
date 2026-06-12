---
title: "Huw to install cedega"
date: 2006-08-03
forum: Gaming &amp; Leisure
---

### Post by Mandalf on 2006-08-03
Hi. Im new on ubuntu and want to installed games. My friend recommended cedega

I got cedega. Huw do I to install it. I got many files

Hers a list:
* cedega-5.1-1.i386.rpm
* cedega-5.1.1-releasenotes.html
* cedega_5.1_i386.deb
* cedega-5.1.tgz
* cedega-engine-5.1.1-local-update.i386.cpkg
* cedega-small-5.1-1.i386.rpm
* cedega-small_5.1_i386.deb
* cedega-small-5.1.tgz
* cedega-small-mandriva-5.1-1.i386.rpm
* cedega-small-suse-5.1-1.i386.rpm

I run on ubuntu 6.06 with KDE

Huw do I to install the program?

---

### Post by Patskumaster on 2006-08-03
You should install "cedega-small_5.1_i386.deb" packet. Command is: sudo dpkg -i cedega-small_5.1_i386.deb

---

### Post by Mandalf on 2006-08-03
> **Patskumaster said:**
> You should install "cedega-small_5.1_i386.deb" packet. Command is: sudo dpkg -i cedega-small_5.1_i386.deb

It not been installed becouse it dont have "xlibs"

---

### Post by tuxcantfly on 2006-08-03
try: sudo apt-get install xlibs

if it doesn't work, do this: sudo apt-get install equivs

equivs-control xlibs

edit the text file so that it says xlibs in package

equivs-build xlibs

sudo dpkg -i ./xlibs-something.deb

---

### Post by Sammi on 2006-08-03
Yeah there are ways around that xlib problem thingy... I remember I had problems and got around them... just don't know how...

Try tuxcantfly's suggestion. Good luck!

---

### Post by Perfect Storm on 2006-08-03
The new version of Cedega package doesn't contain the x-libs issue. If you are on Dapper, just double click the .deb filein gnome and KDE just follow the command shown above.

---

### Post by Mandalf on 2006-08-03
> **tuxcantfly said:**
> try: sudo apt-get install xlibs

if it doesn't work, do this: sudo apt-get install equivs

equivs-control xlibs

edit the text file so that it says xlibs in package

equivs-build xlibs

sudo dpkg -i ./xlibs-something.deb


I can not use: sudo apt-get install xlibs

when i try: sudo apt-get install equivs
It trying to connect to an ubuntu archive. But it does not work. It never been connected

Edit:
Now it works.... not

---

### Post by Mandalf on 2006-08-03
> **Artificial Intelligence said:**
> The new version of Cedega package doesn't contain the x-libs issue. If you are on Dapper, just double click the .deb filein gnome and KDE just follow the command shown above.

I have 5.1.1

---

### Post by Perfect Storm on 2006-08-03
Well, it should also work for v5.1, but why don't grab the latest 5.2.4 instead.

---

### Post by Mandalf on 2006-08-03
I think i done the install now. Huw do I to start the program?

---

### Post by cantormath on 2006-08-03
> **Mandalf said:**
> Hi. Im new on ubuntu and want to installed games. My friend recommended cedega

I got cedega. Huw do I to install it. I got many files

Hers a list:
* cedega-5.1-1.i386.rpm
* cedega-5.1.1-releasenotes.html
* cedega_5.1_i386.deb
* cedega-5.1.tgz
* cedega-engine-5.1.1-local-update.i386.cpkg
* cedega-small-5.1-1.i386.rpm
* cedega-small_5.1_i386.deb
* cedega-small-5.1.tgz
* cedega-small-mandriva-5.1-1.i386.rpm
* cedega-small-suse-5.1-1.i386.rpm

I run on ubuntu 6.06 with KDE

Huw do I to install the program?

you got that off torrentspy, didnt you?

---

### Post by Sammi on 2006-08-03
Busted! :p

---

### Post by cantormath on 2006-08-03
LOL, I totally saw that torrent.......dont get me wrong, I dont mind.

here it is ::grin::
*[size=1]*Not allowed**[/size]

---

### Post by cantormath on 2006-08-03
Cedega Troubleshooting Guide:
[http://downloads.transgaming.com/files/cedega_troubleshooting_5.2.html](http://downloads.transgaming.com/files/cedega_troubleshooting_5.2.html)

Release note:
[http://downloads.transgaming.com/files/cedega-5.1.1-releasenotes.html](http://downloads.transgaming.com/files/cedega-5.1.1-releasenotes.html)
[http://downloads.transgaming.com/files/cedega-5.1-releasenotes.html](http://downloads.transgaming.com/files/cedega-5.1-releasenotes.html)

---

### Post by Perfect Storm on 2006-08-03
Illegal obtained software/piracy and discussion or links aren't allowed. I'm closing this thread.

Mandalf pay for Cedega or use the CedegaCVS version instead, there's a howto/script written by one of our members here on the gaming forum.
Alternative: Use Wine.

---

