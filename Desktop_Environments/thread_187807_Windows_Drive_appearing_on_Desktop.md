---
title: "Windows Drive appearing on Desktop"
date: 2006-06-03
forum: Desktop Environments
---

### Post by crazygerad on 2006-06-03
I got to be able to mount and umount my windows drive and I can read it but in breezy when I did this it appeared on the desktop like it does when you plug a USB drive or a CD/DVD. In Dapper this is not the case. 

This is fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Windows Hard Drive
#/dev/hda1	/mnt/windows	ntfs	ro,users,noauto	#0	0
/dev/hda1	/media/windows	ntfs	ro,users,nls=utf8,umask=0222,noauto	0	0
```

My second problem and this happened in Breezy too is that when it boots up the NumLock, CapsLock and ScrollLock stay lit and not working like expected. I want for NumLock to stay on only and the others to stay unlit. I am using a Belkin Ergonomic USB keyboard.

When I look at Preferences Keyboard:
```
Keyboard Model: Generic 104-key PC
U.S. English
```

Thanks for your help and your time and I hope Ubuntu makes Bill cry :).
PD: The google toolbar works on firefox the spelling help makes my life easier?

---

### Post by Irony on 2006-06-03
Change;

[PHP]/dev/hda1	/media/windows	ntfs	ro,users,nls=utf8,umask=0222,noauto	0	0[/PHP]

to

[PHP]/dev/hda1	/mnt/windows	ntfs	ro,users,nls=utf8,umask=0222,noauto	0	0[/PHP]

You will of course have to first;

[PHP]sudo mkdir /mnt/windows[/PHP]

Then do;

[PHP]sudo mount -a[/PHP]

which will reload fstab.

Note stuff that is mounted in media will appear on the desktop hence changing it to mnt (or any other folder for that matter)

---

### Post by beameup on 2006-06-03
And the GUI way:

Applications > System tools > Configuration Editor >/apps/nautilus/desktop/volumes_visible

Check it to show or not show mounted volumes.

I was looking at the numlock config just a few days ago and I can't find it at the moment. ](*,) (It's that "over 40" thing maybe?) I use the keypad a lot and that's how I like it too.

---

### Post by crazygerad on 2006-06-03
How do I get nautilus?
I used automatrix and it fixed the numLock thing and the other lights. So using the NumLock fixes should help you.

As for the drive not appearing on the desktop, it still doesn't appear. I dont think I have nautilus here.

---

