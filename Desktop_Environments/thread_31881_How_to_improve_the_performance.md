---
title: "How to improve the performance?"
date: 2005-05-05
forum: Desktop Environments
---

### Post by Zonkle on 2005-05-05
Hi,

I'm running Ubuntu on my Asus Laptop which has only 128MB ! And sometimes it gets really slow :( .. is there like any way to improve the performance?

Thanks a lot.

---

### Post by liljencrantz on 2005-05-05
[QUOTE=Zonkle]Hi,

I'm running Ubuntu on my Asus Laptop which has only 128MB ! And sometimes it gets really slow :( .. is there like any way to improve the performance?

Thanks a lot.[/QUOTE]
 If you only have 128 MB RAM, that is probably the biggest bottleneck. You should consider buying a memory upgrade. 

There are some things you can do to decrease memory usage, however.

One thing you can do to increase the performance is to remove the wallpaper. Since the wallpaper is stored twice in memory, this takes up quite a bit of space. (At least this used to be the case)

You can also try out a lean window manager instead of a huge desktop environment. Try using wfce. 

Make sure you're running lightweight programs. Do not run Mozilla. If you run Firefox and use the flash plugin, you _need_ to install the [Flash blocker. ]("http://flashblock.mozdev.org")
Flash leaks RAM like there is no tomorrow. 

You can also try 'tweaking' your system. Use programs like top and xrestop to find the biggest memory users on your system, and see if they can be removed. This should only be done as a last resort, since it will probably buy you very little.

---

### Post by Professor X on 2005-05-05
Gnome performance is going to be rough with only 128MB RAM.  I recommend installing XFCE.  If that's still too slow, install fluxbox.

---

### Post by Buffalo Soldier on 2005-05-05
From the Top Panel, go to:

System -> Help -> Desktop -> System Administration Guide -> Improving Performance

Perhaps you can visit the [What can I remove to improve performance?](http://ubuntuforums.org/showthread.php?t=25406) and [Boosting performance on slow computer](http://ubuntuforums.org/showthread.php?t=13619) threads.

---

### Post by bored2k on 2005-05-05
[http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink](http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink)
[http://ubuntuforums.org/showthread.php?t=25274&highlight=prelink](http://ubuntuforums.org/showthread.php?t=25274&highlight=prelink)

1. Enable Prelink
2. Install XFCE or FLuxbox or IceWM
3. Avoid big programs like OpenOffice, use Abiword and GNumeric
4. Get more ram

---

