---
title: "WiFi problem with XPS 1530"
date: 2008-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thatfunkymunki on 2008-07-08
Hey guys, I just installed ubuntu on my XPS 1530, and it seems that every other boot (literally) my wireless card simply does not exist. ifconfig reports that only my wired card is installed, and lsmod shows that iw3495 is loaded and working. However, once I reboot, it works out of the box. Upon another reboot, the issue reappears. Anyone know what the issue is so maybe I can fix it myself, or have a fix for it?

---

### Post by bigken on 2008-07-08
could badly seated card try pulling it out and reseating

---

### Post by thatfunkymunki on 2008-07-08
I don't think that's the issue, in windows it works 100% of the time. I think I'm gonna try ndiswrapper. I was also looking through dmesg, and I found an interesting message from the iwl3495 module saying something about the card being in MAC sleep mode, I wonder if that has anything to do with the issue i'm describing?

---

### Post by thatfunkymunki on 2008-07-08
(sorry for the double post x_x)

Also, another thing I just tried is removing the iwl3495 module, but it keeps saying it doesn't exist even though it is showing up in lsmod.

---

### Post by bigken on 2008-07-08
You have searched the forum for dell XPS wireless issues


[http://ubuntuforums.org/showthread.php?t=844863&highlight=dell+XPS](http://ubuntuforums.org/showthread.php?t=844863&highlight=dell+XPS)

---

### Post by thatfunkymunki on 2008-07-08
Yeah, I did, and upon searching again, I found what I needed.
[http://ubuntuforums.org/showthread.php?t=707741&page=2](http://ubuntuforums.org/showthread.php?t=707741&page=2)
Thanks very much bigken for your help.

---

