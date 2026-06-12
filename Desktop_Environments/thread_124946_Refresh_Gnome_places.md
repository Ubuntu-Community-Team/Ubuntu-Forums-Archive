---
title: "Refresh Gnome places"
date: 2006-02-02
forum: Desktop Environments
---

### Post by jkwarras on 2006-02-02
Hi,

This is my first post in these forums, I'm new to Ubuntu Breezy (installed 1 week ago) and learning everyday :)

I have a little problem with my mounted devices. It's been some days since they don't show up in the desktop, or in "Computer", or in places. Browsing these forums I show that using this will work:

```
sudo /etc/init.d/dbus restart
```

And it does, the devices are mounted and displayed under places, in the desktop, etc... But when I reboot they don't show up again, and I have to execute the code again to see them in the desktop, places, etc...

Any idea will be great appretiated. **Thanks a lot in advance.**

_PS:_ I also have the problem that cd's are not mounted automatically when inserted, so they're not displayed in the desktop. I can access them via the link in "computer", but I thought that gnome did it automatically and place an icon in the desktop, but I'm not sure.

In case this help here's my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /media/boot     vfat    rw,auto,gid=100,umask=0007,fmask=0117,utf8        0       0
/dev/sda2       /media/winxp32  ntfs    auto,ro,exec,users,dmask=000,fmask=111,nls=utf8        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda4       /media/data     vfat    rw,auto,gid=100,umask=0007,fmask=0117,utf8        0       0
/dev/sdb1       /media/video    vfat    rw,auto,gid=100,umask=0007,fmask=0117,utf8        0       0
/dev/sdb2       /media/swapxp   ntfs    auto,ro,exec,users,dmask=000,fmask=111,nls=utf8        0       0
/dev/sdb3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

### Post by jkwarras on 2006-02-04
> **jkwarras]
I have a little problem with my mounted devices. It's been some days since they don't show up in the desktop, or in "Computer", or in places.[/quote]

Ok, I've found a solution for that :)

I just needed to add me to the 'hal' group. Now that works. I also add me to the 'disk' group said:**
> 
_PS:_ I also have the problem that cd's are not mounted automatically when inserted, so they're not displayed in the desktop. I can access them via the link in "computer", but I thought that gnome did it automatically and place an icon in the desktop, but I'm not sure.

Unfortunely I can't get this working unless I specify intot the fstab to automount the cdrom devices, but this onl work on startup if a cd/dvd is inside the device). For cds inserted once the system is running, I have to go into computer and click on the cdrom link, then the device is mounted and the icon goes into the desktop. Maybe I'm wrong and this is supposed to work like this, not a big deal anyway :)

---

