---
title: "Linux Interferes With Windows"
date: 2006-01-07
forum: Desktop Environments
---

### Post by UltraSonicSite on 2006-01-07
I have noticed this as of right now, and as of a few months ago, that my ***Windows 98*** OS is beginning to become damaged from operations done in linux. Basically, the more I use linux, the more Windows begins to be less effecient.

[CENTER]Here are a few screenshot of a few specific locatons with errors, outlined in red boxes:

[CENTER][URL=http://img432.imageshack.us/my.php?image=screen16az.png]
[IMG]http://img432.imageshack.us/img432/3808/screen16az.th.png[/IMG][/URL]
[[IMG]http://img371.imageshack.us/img371/8558/screen36ib.th.png[/IMG]](http://img371.imageshack.us/my.php?image=screen36ib.png)
[[IMG]http://img371.imageshack.us/img371/2131/screen48lr.th.png[/IMG]](http://img371.imageshack.us/my.php?image=screen48lr.png)

[img]http://img.photobucket.com/albums/v64/ultrasonicsite/screen2.jpg[/img][/CENTER]

Anyone have any fixes, previously on my last install I noticed that all my windows icons stopped working completely. I have since then re-installed windows 98, but now it is starting to act up again. Is Windows jelly of Linux, or is there some issues with both os's running on the same hardrive (2 partitions, 1 windows - 1 linux)

**keywords: windows interferes linux messes up stop working un-usable unusable **

---

### Post by superm1 on 2006-01-07
I won't doubt the more you use linux, the more you _*realize*_ that windows is inefficient.

Unless you have your windows partition mounted in linux and are actively making changes to it or improperly unmounting it - or rebooting with it still mounted this is **impossible.**  Nothing on your windows partition will be affected unless you have actually written to that partition in linux.

---

### Post by UltraSonicSite on 2006-01-07
Any clue to what may be messing it up? I dont want to reinstall window, it's a pain in the ass doing so.

---

### Post by taurus on 2006-01-07
Do you modify or save files to your 98 while you are in Linux?  You have to be a little more specific so people would know what's wrong with first...

---

### Post by UltraSonicSite on 2006-01-07
Well lets see, the only thing I can see messing up my windows is **Wine**...
See, I downloaded this winesetup thingy and it asked for a directory, eh, I picked C:

=P

Heh, then eh thats all I can think of, I didnt boot into windows BEFORE doing that so I have no way of figuring out wether that is it or not.

---

### Post by taurus on 2006-01-07
Maybe you allow wine to write to your Windows' partiton (C:) and mess it up in the process...

---

### Post by superm1 on 2006-01-07
So - again, do you have your windows partition mounted in linux or not?

Could you post the results of whats in your /etc/fstab
(run **cat /etc/fstab**)

Also could you post the results of your normally mounted thing in linux
(run **mount**)

---

### Post by UltraSonicSite on 2006-01-07
[quote='mount']/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)[/quote]

and

[quote='fstab']# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/quote]

---

### Post by UltraSonicSite on 2006-01-07
???

---

### Post by superm1 on 2006-01-07
The windows partitions aren't being mounted.  Everything being done in linux is completely seperate from windows.  Even if you did something in WINE, the settings will remain only on the linux partition.  Whatever is occurring in windows is meerly coincidental.

You may want to check if you hard drive may be going bad or something else that might be causing corruption in windows.  Use a utilitiy like DFT (Drive Fitness Test) for that.  I'm not sure what else would cause such a thing.

---

