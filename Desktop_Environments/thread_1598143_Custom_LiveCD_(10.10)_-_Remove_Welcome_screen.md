---
title: "Custom LiveCD (10.10) - Remove Welcome screen"
date: 2010-10-16
forum: Desktop Environments
---

### Post by Bucky2090 on 2010-10-16
I want to build a custom LiveCD without the Welcome screen at startup. How do I remove the Welcome screen so my LiveCD boots right into a live session without having to click on the 'Try Ubuntu' button? Can't find the answer to this question anywhere.

MGS

---

### Post by Bucky2090 on 2010-10-25
I figured it out. In order to remove the Welcome screen and the Install Ubuntu shortcut on the desktop you must remove the ubiquity installer from you custom LiveCD. 
sudo apt-get purge ubuiquity

MGS

---

### Post by sikander3786 on 2010-10-25
> **Bucky2090 said:**
> I figured it out. In order to remove the Welcome screen and the Install Ubuntu shortcut on the desktop you must remove the ubiquity installer from you custom LiveCD. 
sudo apt-get purge ubuiquity

MGS
If you want to use the disc as an installation media, you'll obviously need ubuquity. Or you'll have to install it in every Live session.

---

### Post by alanmoore78 on 2010-10-25
That's awesome, Bucky!  This may come in handy for me as I try things out on various computers around the home (and around town...the lady at the water department is pretty computer illiterate and asked me about Ubuntu since she heard of it from the whole 10-10-10 thing).

THANKS!

---

### Post by tpackage on 2011-02-13
> **Bucky2090 said:**
> I figured it out. In order to remove the Welcome screen and the Install Ubuntu shortcut on the desktop you must remove the ubiquity installer from you custom LiveCD. 
sudo apt-get purge ubuiquity

MGS

I think you may have the spelling wrong for ubiquity.

ie. sudo apt-get purge ubiquity

---

