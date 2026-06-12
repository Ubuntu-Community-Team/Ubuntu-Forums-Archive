---
title: "beryl decorations disappear"
date: 2006-10-18
forum: Desktop Effects &amp; Customization
---

### Post by engineer on 2006-10-18
my window decorations disappear, when i stretch windows to about 95% of screenwidth. is anyone else having this behaviour?

beryl version 0.1
X: aiglx with radeon open source driver (mobility m6 ly)
the rest: edgy standard versions

---

### Post by engineer on 2007-01-17
now i changed the "agpsize" parameter in the "device" section of my xorg.conf form 16 to 32 and everything works!

```

Section "Device"
    Option    "AGPSize"    "32"
EndSection

```

---

### Post by phineaus on 2007-05-10
Bravo!  I have this same video driver, except my substandard card is indeed a 16mb version in my Toshiba Satellite S301.  Boo.  However, I wrote this option into my xorg.conf, and no more problems.  Actually, I had not installed Beryl on this machine precisely because of the crappy card, but it appears to work fine now...with the options I want out of Beryl at least.  I will make sure and post back if my video card fries from what I am assuming is a configuration overload.  
Thanks,
phineaus

---

