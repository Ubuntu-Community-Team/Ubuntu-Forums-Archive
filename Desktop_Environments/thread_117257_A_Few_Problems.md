---
title: "A Few Problems"
date: 2006-01-14
forum: Desktop Environments
---

### Post by DigitalDuality on 2006-01-14
This forum has been helpful so far and i don't want to clutter it up with a few.. what is probably, simple problems.  I got this machine almost completely ready to use for my weekly functions but there's a couple of problems left.

Totem will not play DVDs.  It's asking for a libdvdcss file or installation, and have no idea where i get that.

Totem plays all my video files, but they color quality is a bit off. It's not intolerable as i've always watched 3 full legnth documentaries on it and got by just fine.  The video seems to be a bit too bright though.  I can't find a way to change that.

VLC will not play sound, though it'll play video on everything it is supposed to.

I installed the newest firefox.  But i don't know how to get rid of the old one.  it would probably be nice to know how to edit the Applications menu as well.

If anyone can help on any of these issues, i'd be very grateful :)    I'm loving Ubuntu so far and it's been a damned good experience

---

### Post by Ptero-4 on 2006-01-14
libdvdcss is a non-free codec required to play comercial DVD's.
About editing the applications menu. Use smeg, it's included in breezy.

---

### Post by DigitalDuality on 2006-01-14
Gracias on the smeg. :)

Still can't find where to get the right version/copy of that codec.

---

### Post by drummer on 2006-01-14
How to install libdvdcss is in here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) as well as many other tips for getting multimedia running. For VLC, try installing a different sound backend for it. I think the packages are something like vlc-esd, vlc-alsa, etc., choose the one you want and try others if one doesn't work.

---

### Post by DigitalDuality on 2006-01-14
Kudos. That fixed my VLC problem.

Still can't play my DVDs but i'm sure i'll figure that out with the link you provided. :)

---

### Post by aysiu on 2006-01-14
Didn't you post the same thing [here](http://www.ubuntuforums.org/showthread.php?t=117241)? Please don't double-post. Then you get a lot of redundant help.

---

### Post by DigitalDuality on 2006-01-14
Wow.. my mistake.. my browser froze when i posted that and when i went and looked for it i could find it.  DIdn't mean to do that intentionally.

---

### Post by Mr_Grieves on 2006-01-14
I used automatix to get all neat-o video codecs :D
[http://www.ubuntuforums.org/forumdisplay.php?f=77](http://www.ubuntuforums.org/forumdisplay.php?f=77)

---

### Post by cotcot on 2006-01-15
You can get libdvdcss on the plf website : [http://plf.zarb.org/about.php](http://plf.zarb.org/about.php)

For example be adding to your /etc/apt/sources.list the following reps :

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

and do an apt-get update.
You will find libdvdcss,  wincodec32 and others

---

