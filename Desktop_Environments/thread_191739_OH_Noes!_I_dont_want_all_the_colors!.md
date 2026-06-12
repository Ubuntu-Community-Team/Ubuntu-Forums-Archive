---
title: "OH Noes! I dont want all the colors!"
date: 2006-06-07
forum: Desktop Environments
---

### Post by honeydew on 2006-06-07
o noes!! weirdness on laptop.. this has happend twice now... once I went to logout.. and the other time when xorg was started..   my screen procedes to flash thru a series of colors.. when it hapened on the log out I was lucky enough to be able to ctrl+alt+bkspace, when this occured I wasnt aple to switch to any tty interface.. I was forced to hold down the power button.. any ideas.. Ill post logs if anyone wants to see any..

---

### Post by mscman on 2006-06-07
Have you tried just letting this "weirdness" procede for a few seconds?  My laptop continues to draw strange colors on a fairly regular basis, particularly when X is starting or stopping (this is always the case when going to/from hibernation.)  I'm not sure what exactly the cause is, but on my computer it hasn't caused any serious problems.  It is something that someone may find disturbing though.

Not sure if you're referring to this slight glitch or a more prolonged problem, although you do mention that it was completely locked up at one point.

---

### Post by honeydew on 2006-06-07
no.. prolonged.. like... I didnt sit thru it for more then 30 seconds or so.. but the whole screen will flash green... then blue.. then red... then white.. or some arrangment of colors..  on boot up, while it was flashing I heard gdm.. and attempted to type in my login/password, I was successful in this cause I heard the ubuntu bells.. but the screen was still flashing colors... no sign of any usable os underneath..

---

### Post by honeydew on 2006-06-08
harrrhummm

---

### Post by mscman on 2006-06-08
What graphics drivers are you using (and what graphics card)?  Have you tried switching to the generic VESA drivers to see if it makes any difference?

---

### Post by honeydew on 2006-06-08
Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Grap$        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

^from my xorg.conf

so.. for this instead of 810 I should replace it with

Driver "vesa"

?

---

### Post by mscman on 2006-06-08
[QUOTE=honeydew]so.. for this instead of 810 I should replace it with

Driver "vesa"[/QUOTE]
I would to at least see if it makes any difference, you can always switch it back later.

---

