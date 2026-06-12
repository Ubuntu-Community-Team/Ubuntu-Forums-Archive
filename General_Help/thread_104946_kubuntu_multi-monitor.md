---
title: "kubuntu multi-monitor"
date: 2005-12-17
forum: General Help
---

### Post by gts on 2005-12-17
I have 2 crt monitors (sx 15'' 800x600, dx 19'' 1280x1024) on a Radeon 9800 pro, and I would like to have a unique desktop area extended in these monitors; the problem is that I can setup a single area only with monitors that are of the same dimension, and that's not my situation; the alternative is to have 2 completely separated desktops, but I can't move windows from a monitor to another...

Sorry for my english... 

Any ideas?

---

### Post by ad noiseam on 2005-12-17
I have another Radeon, and two screens with the same resolution, so I am not sure that this will help you, but have a look at my xorg.conf file at this end of this thread:
[http://ubuntuforums.org/showthread.php?t=55074&page=2&highlight=xinerama](http://ubuntuforums.org/showthread.php?t=55074&page=2&highlight=xinerama)
it works great under Kubuntu.

---

### Post by kb3hkg on 2005-12-20
You may want to look into this thread, its about the 9600 but i know it worked on my 9700 and it may work on other ati cards as well, it switched you from the standard ati driver to the fglrx driver

[http://www.ubuntuforums.org/showthread.php?t=101293](http://www.ubuntuforums.org/showthread.php?t=101293)

---

### Post by adie273 on 2005-12-21
It is possible to do this by editing the xorg.conf file and using xinerama.

Both monitors can be at any resolution as I have done it before on another system.

But your xorg.conf file needs to be edited spot on first time round, or if like myself you make 1 stupid little mistake, the monitors won't show anything at all next time you boot ubuntu lol ](*,) 

Adie

---

### Post by shakin on 2005-12-21
If you use the fglrx setup program (can't remember the name of it) to generate an XF86Config file you can copy the monitor, vid card and screen sections out of that.

The setup program will ask if you want to setup multi-monitor mode. Two options are Big Desktop and Dual Head. Big Desktop mode is where your desktop stretches so it effectively operates like a single widescreen monitor. Dual Head is the separate desktop mode where you cannot drag windows between monitors and each monitor will have its own system tray, task bar and K menu.

Both modes support running each monitor at a different resolution from the other. I don't think Xinerama supports that, which might be where your trouble is. You don't need Xinerama at all since the ATI driver handles that function.

---

