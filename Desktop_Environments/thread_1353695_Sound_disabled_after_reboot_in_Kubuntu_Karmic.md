---
title: "Sound disabled after reboot in Kubuntu Karmic"
date: 2009-12-13
forum: Desktop Environments
---

### Post by MaximeG on 2009-12-13
Hi Ubuntu Folks,

The issue I'm facing is regarding sound.
I've installed Kubuntu 910 a couple days ago and it worked flawlessly, sound included.

I've then upgraded the kernel from *.31-14 to *.31-16, worked fine after the first reboot, but not after the second !
Same thing happened after another kernel upgrade from 16 to 17.

This is quite annoying especially since I really don't know where to have a look at in Ubuntu. 

My lspci can see the cards : 

```
maximeg@DreamTheater:~$ lspci | grep -i "[aA]udio"
04:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
0a:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
```but it looks like no alsa modules are loaded :

```
maximeg@DreamTheater:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```Also, KDE can't see my sound devices in the list of available devices (greyed out as they were previously available.)

Thanks a lot,
Maxime

---

### Post by MaximeG on 2009-12-13
*Bump* : Simplified post.

---

