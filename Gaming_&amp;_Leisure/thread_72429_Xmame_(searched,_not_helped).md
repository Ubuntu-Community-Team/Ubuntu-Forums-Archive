---
title: "Xmame (searched, not helped)"
date: 2005-10-06
forum: Gaming &amp; Leisure
---

### Post by duffydack on 2005-10-06
apt-get install xmame
cant adjust the tiny screen size and cant go full screen (using ATI 3D driver in xorg if that matters)
compiled advmame and get
advmame dkong
AdvanceMAME - Copyright (C) 1999-2003 by Andrea Mazzoleni
MAME - Copyright (C) 1997-2003 by Nicola Salmoria and the MAME Team
Unable to initialize the video driver. The errors are:
fb: Unsupported in X.

have read that GL can do fullscreen, great, where is it , as apt-get says not there (i have added repos for universe/multiverse and backport).

TIA

---

### Post by KingBahamut on 2005-10-06
Ive had little or no success with xmame/xmess in this aspect. Similarly Ive run into issues with Nestra and Dgen.
 
Ill see what I can dig up for you though duffy.

---

### Post by duffydack on 2005-10-06
well this will do for now.
xmame -x11-mode 3 (gamename)

full screen.. i still cant find xmame-GL and wouldnt know how to use it anyways, as i say x11-mode 3 will have to suffice....thanks.
im nearly there converting to kubuntu fulltime !!!....only thing is i HAVE to use vmware and an XP guest (cant get rid of windows no matter how you try) as i need my Movie Collector and it performs like a friggin joke in WINE...take forever to export my list to HTML, which i do quite frequently. ( I have 900 movies added to it :) )

---

### Post by BoyOfDestiny on 2005-10-07
I've had success with advmame and advmenu in both hoary and breezy. I have made some debs with checkinstall (in breezy with the 2.6.12 kernel)

Here ya go! (and yes I have an ati card to, tested with open source driver and fglrx)

debs:
[http://www.safaribans.com/gpl/advancemame-0.99.0-1_i386.deb](http://www.safaribans.com/gpl/advancemame-0.99.0-1_i386.deb)
[http://www.safaribans.com/gpl/advancemenu-2.4.10-1_i386.deb](http://www.safaribans.com/gpl/advancemenu-2.4.10-1_i386.deb)

sources:
[http://www.safaribans.com/gpl/advancemame-0.99.0.tar.gz](http://www.safaribans.com/gpl/advancemame-0.99.0.tar.gz)
[http://www.safaribans.com/gpl/advancemenu-2.4.10.tar.gz](http://www.safaribans.com/gpl/advancemenu-2.4.10.tar.gz)

Tip: install advmame before advmenu (since it will then auto detect it)
advmenu is great and multiplatform (I just don't like the sounds etc) so I recommend you edit the .rc (should be in /home/.advance) or something (not at my laptop right now)

---

