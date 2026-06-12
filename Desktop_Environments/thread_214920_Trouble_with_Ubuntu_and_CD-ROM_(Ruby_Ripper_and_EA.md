---
title: "Trouble with Ubuntu and CD-ROM (Ruby Ripper and EAC)"
date: 2006-07-13
forum: Desktop Environments
---

### Post by citizenkeith on 2006-07-13
Ok, I have a new installation of Ubuntu 6.06. I have no problem opening up an audio CD in Sound Juicer. But I just installed RubyRipper, and also EAC via Wine, and none of them can recognize the CD drive. Actually, RubyRipper can partially recognize the CD. It will display the CD title and the artist and title, but under Status, it says "No disc found in /dev/hdc." I tried changing the CD-ROM location to /media/cdrom0 and that didn't work either.

EAC just doesn't display anything. I have the preferences set to "Installed external ASPI device" because the other options are not available. In winecfg, I have drive E set to /dev/hdc, with type CD-ROM and Autodetect from Device checked. Still nothing in EAC.

Here's my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1	/media/windows	ntfs  nls=utf8,umask=0222 0 0
/dev/hdd1	/media/windows2 vfat iocharset=utf8,umask=000 0 0

```

Any help would be appreciated.

Keith

---

### Post by citizenkeith on 2006-07-13
bump :)

---

### Post by orb9220 on 2006-07-13
Did you winecfg for the apps
alt+f2
winecfg

Is app listed in applications tab then select app.
click on drives tab is cdrom listed there?
If not click on Autodetect.
Apply and try.

Still don't work start at top and get back to drives and under autodetect click on advanced click on type drop down and select cdrom click apply then ok and try again.

Just making some guesses at the problem. Also if I remember right there are other threads. Just do search for EAC

Hope this helps.
](*,)

---

### Post by citizenkeith on 2006-07-13
Thanks for the tips. I've tried all of your suggestions, and nothing worked. :(

---

### Post by citizenkeith on 2006-07-15
Still in need of help...

---

### Post by citizenkeith on 2006-07-16
bump

---

### Post by waldbauernbub on 2008-03-17
I solved the problem:
EAC doesn't recognize my CD drives and I am not able to select the "Native Win32 Interface for NT/2000/XP" in the EAC interfaces option
(as described in [http://ubuntuforums.org/showthread.php?t=142784](http://ubuntuforums.org/showthread.php?t=142784) )

under the drive tab in Alt+F2 winecfg I had 3 CD-drives listed although I only have 2 installed:
K: /media/cdrom0
L: /media/cdrom1
M: /media/cdrom2 (this is the drive that doesn't exist)

I deleted the third drive (in the wincfg) and now I can apply the all setting in EAC and have just ripped my first CD under Ubuntu.

Attention: Maybe this third drives serves any purpose I am not familiar with.

much luck
harald

---

