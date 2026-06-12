---
title: "ArtS sound under Hoary GNOME?"
date: 2005-08-29
forum: Desktop Environments
---

### Post by jamyskis on 2005-08-29
OK, here's the problem. I use GNOME under Hoary and have a Logitech USB Headset. All applications work with it with the exception of one - Skype. Being a KDE application, I would imagine that it's trying to access sound through ArtS. I've set Skype to access  /dev/dsp1 (which I think is the headset, although difficult to say for sure) as using /dev/dsp just crashes Skype. I've also tried using the ESD client (esddsp) to run Skype but that's not helped either.

Does anyone have any suggestions as to where the problem might lie?

Best regards,

D

---

### Post by grim42 on 2005-08-29
See this HOWTO to solve your problem:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

---

