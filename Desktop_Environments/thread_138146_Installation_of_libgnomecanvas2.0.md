---
title: "Installation of libgnomecanvas2.0"
date: 2006-03-01
forum: Desktop Environments
---

### Post by awreneau on 2006-03-01
I'm new to KUBUNTU, came from Debian.  Very nice!

Anyway onto the problem.  Installing Automatix and following the instructions from the newbie section I ran into a problem, cant install libgnomecanvas2.0.


*******error ************
sudo apt-get install libgnomecanvas2.0

Couldnt' find package libgnomecanvas2.0
******end error**********

This is odd, becase yesterday I did this, and it worked fine no problems whatsoever.  Liked it so much I decided to install it on a 2nd machine, but it fails with the above, obviously paraphrased, error.

Has this package been renamed, removed?  apt-cache search doenst produce any results nor does using Adept.

Suggestions?

Thanks

---

### Post by Jucato on 2006-03-01
try using libgnomecanvas2-0 instead of libgnomecanvas2.0

You can use wildcards to help your apt-cache search:
```
apt-cache search "search_pattern"
```
In my case, I typed:
```
apt-cache search "libgnomecanvas*"
```

---

### Post by awreneau on 2006-03-01
I'll give that a shot, from what I can tell thusfar Kubuntu is pretty much identical to Debian, but I'm treading lightly.

Thanks very much for the advice. I'll post back my findings.

WR

---

### Post by Jucato on 2006-03-01
[QUOTE=awreneau]I'll give that a shot, from what I can tell thusfar Kubuntu is pretty much identical to Debian[/QUOTE]

Well, probably because Ubuntu is Debian-based?

---

### Post by Ptero-4 on 2006-03-01
Isn't libgnomecanvas2.0 part of gnome. I ask b/c he says he have kubuntu and if that lib is part of gnome then automatix is probly trying to install ubuntu-desktop or parts of gnome. Also a question. Does automatix work on PPC? and does it recognizes if you got kubuntu instead of ubuntu and installs the kde baed equivalents of the gnome specifics like the xine frontends?

---

### Post by Jucato on 2006-03-01
I'm pretty sure the name of the package is libgnomecanvas2-0.
Yes, it's a GNOME library which is used for many GNOME apps, totem and rhythmbox to name a few.
I'm not sure if Automatix would work on PPC.
Automatix installs software irregardless of your desktop environment. Some examples of the things that it installs: firefox 1.5, propriety codecs (w32codecs), flash and java, wine, and some other things I can't remember. 
I'm not sure what program he was trying to install from Automatix that would need libgnomecanvas, though. Automatix, anyway, is just supposed to automate the downloading and installation of some "commonly used" software,codecs, plugins. But these you can still do manually.

---

### Post by awreneau on 2006-03-02
Fenyx, thanks for stating the obvious, I know that Kubuntu was based on Debian.  There are instances where a flavor will come out with it's own (insert package name here) that will break from the "traditional" way of doing things.

Anyway, I changed my configuration and made the machine a dual boot w/ XP and Kubuntu.  And tried everything works fine now, now sure what the problem was.

Thanks for the input!

Little tid bit, I've tried the major Distros, Debian, Fedora, Mandriva, SuSe and Slackware even tried FreeBSD.  Kubuntu has been the most rewarding and so far the most reliable.  The only exception that I've seen, this may be due to limited time with it, is that it didnt do everything that Xandros did.  Xandros was/is a little more aggressive about integrating with a Windows environment but I wasnt interested in integrating and when I am I can mount samba shares on my own.  

So, I may have finally settled.  I'm sure you will all sleep better knowing this huh?;) ;)

---

