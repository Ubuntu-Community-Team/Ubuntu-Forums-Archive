---
title: "Compiz makes my boot slowwwwww"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by airbornemist6 on 2008-01-16
I have a problem, after installing Compiz from git (using[ this]("http://ubuntuforums.org/showthread.php?t=643485") guide). Now when I boot, after going past gdm, loading the sound, and desktop search, startup stops for about 3-4 minutes. During this time, there is no resource usage, the CPU is idling at 0-4% and I have no window borders if I load a window. After 3-4 minutes, though, network monitor, fusion icon, and my other bootup programs load almost instantly. I've tried looking in the system log, but when I look, I just see 3-4 minutes of blank space. This makes no sense to me, does anyone know what caused it/how I might fix it?

---

### Post by UbUsOsOlik on 2008-01-17
i think you have a problem with open gl, Try reinstalling the compiz (ccsm) utility or try reinstalling you drivers. Hope this helps, i kind of had the same problem and this helped me.

---

### Post by airbornemist6 on 2008-01-17
you see, that doesn't work, I've tried it, and I've also had this problem on a clean install. It seems to be a problem with something the guide does... I just don't know what exactly.

---

### Post by Espreon on 2008-01-17
> **airbornemist6 said:**
> you see, that doesn't work, I've tried it, and I've also had this problem on a clean install. It seems to be a problem with something the guide does... I just don't know what exactly.

Maybe CF hates you, because when I used my guide on my comp I do not experience these dramatic slow downs...
If you think it has to do with the guide maybe look at the makefusion script...

---

### Post by Sef on 2008-01-17
What are your system specs?

---

### Post by airbornemist6 on 2008-01-18
I'm using an HP laptop

250 GB HDD
GeForce 7150M
Turion 64 X2-58
2GB RAM
15.4" LCD screen

EDIT:
BTW, Espreon, I don't think it necessarily has to do with anything you did wrong. I think compiz fusion might actually hate me, but I still want to get it to work.

---

### Post by sensimilla on 2008-01-18
I've been getting the same thing.
Startup stalls for exactly 2 minutes just before the gnome session startup programs are run.

Athlon X2 3800
Geforce 8800gt 169.07 driver
1.75 GB ram
lots of harddrives...

kernel 2.6.22-14-generic
Ubuntu 7.10 (upgraded) from 7.04

---

### Post by airbornemist6 on 2008-01-23
Ok, completely different hardware, I guess it doesn't have anything to do with my hardware. Well, it could, but doesn't look like it at the moment.

EDIT:

Uninstalled it and then upgraded to hardy, problem solved xD

---

