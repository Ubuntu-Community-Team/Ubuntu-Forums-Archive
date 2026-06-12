---
title: "Plying rm file in XMMS"
date: 2006-09-23
forum: Desktop Environments
---

### Post by marufsiddiqui on 2006-09-23
Well I wanna know can XMMS play real media ie rm, ram etc file? Is there any file (pluging) available for.

Another thing-- still no solution regarding offline installing. I am wanting help again. I have download all dependency files of MPlayer & copied them to my home folder in "/home/ubuntu/packages" , Now what to do ? I cant install it. I have thought about another alternative---its like I download the necessary files & then write in a cd and then add the cd in respitoris.---is it possible?

Plz plz help me

---

### Post by ajgreeny on 2006-09-23
How are you trying to install it?  Perhaps you will have more luck if you put the package files into /var/cache/apt/archives and try to do the install with *sudo dpkg-install mplayer* which should (I think) deal with everything.

---

