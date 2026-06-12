---
title: "Make bootup faster"
date: 2007-07-11
forum: Desktop Environments
---

### Post by travist120 on 2007-07-11
Hey guys, I've been noticing that ever since I've installed Ubuntu Studio, my bootup always pauses at one point. I completely removed the Latency kernel it came with because it didn't work with my wireless card, and I had no idea how to make it work either. I pressed alt+f1 or f2 or something that let me see a verbose list of what's going on during bootup and I saw that it was trying to resume some image, but can't find so it says "Doing normal boot" any idea on how I can fix this? It takes at least 40 seconds to a minute sometimes and I don't know what's going on. The most likely idea for me is that I edit the GRUB boot command line but then again, I have no idea where to point it so that it boots faster. Thanks in advace.

---

### Post by mbsullivan on 2007-07-11
Hi,

It's looking for an image after you hibernate. Failing that, it boots normally. I would suggest leaving this step in bootup if you use hibernate... Otherwise, you could take it out.

An easy way to control what services are started and at what time are to use the sysv-rc-conf perl tool as described [here]("http://ubuntuforums.org/showthread.php?t=89491").

Mike

---

### Post by travist120 on 2007-07-11
ah, I see. Though it's never taken this long before.

---

