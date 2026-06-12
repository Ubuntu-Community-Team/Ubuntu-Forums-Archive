---
title: "Removable Media Issues"
date: 2005-11-19
forum: Desktop Environments
---

### Post by MistaED on 2005-11-19
Hello, I wanted to finally express my annoyances with Ubuntu/Gnome and mounting/handling/etc. of usb/firewire removable media. They all mount ok and I can read them, but I always get quirky behaviour like when I try to write to it, it "instantly" appears on it. But later when I unmount it from the desktop, it does all the copying then. 

HOW DO I GET THIS TO STOP??? I'd like it to copy as I set it to copy. Plus sometimes when unmounting it would just disappear, but copy in the background. So when you pull it out thinking it's unmounted, there goes your important data on that drive. :(

Can anyone help me to disable this feature/bug?

Thank You
-MistaED

---

### Post by MistaED on 2005-11-21
*BUMP* - Please, this is one bug which is causing my friend to go windows! And this friend in theory can do anything he wants in ubuntu as he doesn't play many high end windows games or autocad or any program which is windows-only (other than dvd shrink, but wine/crossover is good with that), just azureus, limewire, kopete, amarok and mplayer/vlc can do everything for him.

I want to add to this, with optical media burnt in UDF mode, these don't mount at all as it seems like the auto-mounter forces iso9660 all the time. Plus when he plugs in his ipod and external 200gb drive and swaps them (one firewire plug) the auto-detection of them fails. In the kernel, it still detects them though (/dev/sda and /dev/sdb for when one device is unplugged and the other plugged in it's place), but there is no auto-mount after this for some strange reason and the computer needs to be powered down for 10 seconds and turned on again for it to mount again.

Thank you and I hope someone can help me out and not just ignore these serious issues with auto-mounting in ubuntu/gnome/linux.

-MistaED

---

### Post by ed_d on 2005-11-21
On the unmount write part, Thats what linux does. I have had the same experiance with floppies too. Just how it works.

---

### Post by RAOF on 2005-11-21
It's much more efficient, and results in less wear on the USB drive.  (Don't some kinds of flash memory have a limited write-lifetime?)

There is a bug in bugzilla about this, though.  There might be some workarounds in the comments.

---

### Post by doclivingston on 2005-11-21
You need to unmount the drive before removing it, you also need to do this on Windows. If you remove the drive without unmounting it (on either operating system) you take the risk of corrupting it.

In theory you can disable the write-cache, so that you can remove it as soon as the copy dialog disappears, however there are a number of problems:
1) copying will be slower
2a) if it's flash-based, it may reduce the lifespan of the device
2b) if it's hard-drive based, it will cause more disk seeks and slow down copying a *lot*
3) some applications may  stop responding while they are writing to the device
4) and some other things


Overall it's a fairly bad idea, and the best solution is to remember to unmount the drive before removing it (and you should do this on Windows too).

---

### Post by MistaED on 2005-11-22
Yes I know to unmount it definitely before removing it, as I've told everyone to do, even on windows. But, it's hard to see this when the device disappears from the desktop after selecting unmount, looking like it did unmount, but it really didn't. I inserted the drive again and saw that there was no committed changes at all, or some files copied partially to it. I heard someone said the sync option is what you need to make actual copying work at the time of doing the copying, but I am unsure where the configuration settings are for gnome-volume-manager to do this.

There is also a bug with gvm where ipods don't unmount cleanly either, or when you plug in another device after it like an external drive, it doesn't get automounted (but the kernel recognises it) when using the same plug (firewire). For now, I just got the ipod plugged into a usb2.0 port instead of changing the firewire one so this isn't a problem anymore.

I understand this approach is very efficient as it only does the committing changes whilst it unmounts, but I can see newbies not knowing this and it turning out to be a very bad situation of corrupted external drives. Plus when there is no indication that it unmounted cleanly, it's very hard to see if it is ok to unplug it.

Plus, I want to modify GVM to figure out how to mount UDF-made cd/dvd's automatically instead of trying to mount them as iso9660 and failing.

Thank you
-MistaED

---

### Post by ren wins on 2005-11-22
for ipods
i hear if you use eject /path/ipodname in terminal, it gets it to unmount
i havent had a chance to confirm/deny this (which is why i dont know the exact path where you find your ipod, i DO know that the ipod name is whatever you named it in windows)

---

