---
title: "Weird font problem in Kubuntu/E17/Entrance"
date: 2007-02-12
forum: Desktop Environments
---

### Post by Guranic on 2007-02-12
I have Kubuntu Edgy in my laptop and recently I've been using Enlightenment (E17) desktop as my WM. (Really great desktop environment for older laptop BTW) Now I installed entrance login manager to save some extra memory for actual applications and everything still works OK but there is one tiny problem with fonts in applications. E17 fonts are working fine but everytime I boot my laptop application fonts are really tiny (like in amaroK or adept manager menubar), so I have to open KDE font config app (kdmshell fonts) and just hit apply and OK to have fonts like they are normally. kdmshell fonts shows everything ok, I don't have to change any setting, just apply/ok. Is there some config file to be loaded in E17 start or what? For now only solution is to go back tu KDM and loose few megs valuable ram. :confused:

After digging some more info I would say that problem is this DPI thing. I add DPI value in xorg.conf but it didn't help, if I change it using KDE gui tool (Fonts) to 96 dpi, fonts will be the way I want them to be. How can I make X start in 96 dpi mode?

---

### Post by Guranic on 2007-02-13
OK. I found solution by myself. According to this post [http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976) I add following lines to xorg.conf like advised in previous Howto. (Uncomment right one) Fonts are nice again and E17 is quick and cool!

```

#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi

```

---

### Post by jay_knight on 2007-03-01
Thanks! This works also for Gnome (obviously) and saved me from removing E17 completely!!

---

### Post by n-alexander on 2008-03-16
> **Guranic said:**
> OK. I found solution by myself. According to this post [http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976) I add following lines to xorg.conf like advised in previous Howto. (Uncomment right one) Fonts are nice again and E17 is quick and cool!

```

#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi

```

did this, but still

>xdpyinfo | grep dimensions
dimensions: 1024x768 pixels (491x368 millimeters)
>xdpyinfo | grep resolution
resolution: 53x53 dots per inch
>

and all Gnome applications show up in very small fonts for menus and all. 

Tried to chance numbers in xorg, but it doesn't seem to affect resolution in any way, it stays 53dpi. Why could that be?

---

