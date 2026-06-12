---
title: "ubuntu becomes so slow after using for a while"
date: 2007-07-07
forum: Dell  Ubuntu Support
---

### Post by mesocool on 2007-07-07
I install ubuntu 7.04 on my dell 700m laptop. Recently, I found that it becomes so slow after I use it for a while especially when using netbeans or evince. The whole computer is almost frozen and the hard drive runs like crazy. I have to reboot my computer in order to use it again. I didln't see anything taking much memory with 'top -i'.

Anybody has ideas what's going on? Ubuntu works fine on my desktop.

Thanks..

---

### Post by jrusso2 on 2007-07-07
I would suspect one of those two programs is using a lot of cpu or a lot of memory

---

### Post by mesocool on 2007-07-07
> **jrusso2 said:**
> I would suspect one of those two programs is using a lot of cpu or a lot of memory

Thanks. But they both work fine on my desktop.

---

### Post by HermanAB on 2007-07-07
With top, do you see kerneld running?

If so, then the machine is swapping to/from disk.  The solution is to add more memory or to run a different desktop system that doesn't chew up all so much resources, eg. IceWM, instead of Gnome/KDE.

Cheers,

Herman

---

### Post by mesocool on 2007-07-10
> **HermanAB said:**
> With top, do you see kerneld running?

If so, then the machine is swapping to/from disk.  The solution is to add more memory or to run a different desktop system that doesn't chew up all so much resources, eg. IceWM, instead of Gnome/KDE.

Cheers,

Herman

Thanks, I tried IceWM and it did seem to be faster than gnome, at least on GUI booting time. But it still froze my machine once I launch 2 or more java applications like Netbeans. Maybe I just stick with my terminal for Java development. 

But my xp seems working a little better with Netbeans. Maybe its memory management is better? I have 512M memory and it is a Pentium M machine. :(

---

