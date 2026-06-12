---
title: "cdrom on desktop twice"
date: 2007-09-04
forum: Desktop Environments
---

### Post by schickb on 2007-09-04
I am running Ubuntu Feisty AMD64 on a Athlon X2 machine with a single Plextor DVDR PX-740A drive.

When I boot my machine and login to Gnome with a plain non-writable data CD in the drive, I get two icons on my desktop and under "Places" for that one CD. If I eject the CD physically or right-click eject, one of the icons goes away, but the other remains. If I look at the properties of the remaining icon, it looks umounted (shows no volume info).

If I restart X with ctrl-alt-backspace or if l logout and login again, I get only one icon as expected. But the next time I reboot I get two again.

By default the following was in /etc/fstab. I've tried commenting that out but it didn't change anything.

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Any suggestions?

---

### Post by banewman on 2007-09-05
A question - is the hard disk in fstab as sda? it might have - for some reason - mounted the cd as a volume. Try looking in /etc/mtab to see if the cd is mounted twice. :)

---

### Post by schickb on 2007-09-06
Yes, my hard drive(s) are sda, sdb, and sdc. 

But I've since stopped using Beryl and the duplicate icon problem went away. Not sure why that would be releated, but a number of other problems have cleared up since I disabled Beryl as well.

---

### Post by schickb on 2007-09-07
Spoke too soon. The problem is back, but I've noticed that it only happens with certain CDs.

/etc/mtab only shows the drive once. Its the last entry below:

```
desktop-ubuntu:/$ cat /etc/mtab
/dev/sda6 / xfs rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda1 /boot ext3 rw 0 0
/dev/sda7 /media/centos ext3 rw 0 0
/dev/disk/by-uuid/64D06AC2D06A9A56 /media/winxp fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/disk/by-uuid/F66CBBF46CBBAE2D /media/winxp-games fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hda /media/Drivers iso9660 ro,nosuid,nodev,uid=1000,utf8 0 0
```

Under /media I also have a file called .hal-mtab that contains only the cd like this:

```
desktop-ubuntu:/media$ cat .hal-mtab
/dev/hda        1000    0       iso9660 nosuid,nodev,uid=1000,utf8,exec /media/Drivers
```

But its only mounted a single time as /media/Drivers (in this example). Adding /dev/hda to fstab seems to make no difference. I get the same double icon whether that is include in fstab or not. If I remove or umount the drive, it no longer appears in /etc/mtab but one of the icons remains on my desktop. Seems like a glitch in the code that is putting volumes on the desktop automatically (what does that)?

---

### Post by banewman on 2007-09-08
Silly question time
 - Have you double clicked the icon when there is nothing in the drive to see what happens
 - Have you tried dragging it to the garbage bin or right clicking it and moving it to the garbage bin. Might be a start to a solution. :)

---

### Post by schickb on 2007-09-08
While ejected:

* Double clicking says:

Couldn't find "/media/Drivers".
Please check the spelling and try again.

* Right-click properties shows:

On the Basic tab
[INDENT]Name: Drivers
Type: unknown
Size: unknown
Location: on the desktop
All the rest "unknown"[/INDENT]
No info in the Permissions tab
No Volume tab at all

* Dropping it on the trash does nothing. Selecting the icon and hitting the delete key says:

You cannot move the volume "Drivers" to the trash.
If you want to eject the volume, please use "Eject" in the popup menu of the volume.

---

### Post by banewman on 2007-09-08
Trying to sort this out from here requires careful questions : what other icons are on the desktop?
 - that icon that is there on it's own when there is nothing in the drive is listed as /media/drivers or refers to /media/drivers - did you install a driver for cd or dvd or something?
 - Try " sudo chown -v you:you /home/you/desktop/(name of icon) - you = login name Right click will get how the system refers to the icon. This is an attempt to let you put it in trash.

---

### Post by schickb on 2007-09-09
The only icons on my desktop are the names of volumes that have been mounted under /media. That includes the cdrom, two ntfs drives with windows on them, and one ext3 drive with Centos. There are no files under /home/me/Desktop so I have nothing to chown.

The name of the icon on my desktop is "Drivers" becuase that is the CD label  (it actually contains windows drivers). It gets mounted as /media/Drivers, but when ejected that mount point is gone. 

Another interesting point. If I insert a different CD. That new CD appears on my desktop correctly and the old icon continues to exist in a disconnected state. So its always the CD that is in the drive when I first boot that gets stuck there. If I logout and log back in the extra icon goes away. The problem is also fixed if I restart X without rebooting.

Really seems like the problem must be in Gnome with whatever determines which icons to add to the desktop. Thanks for the continued suggestions.

---

### Post by reset3x on 2007-09-09
I has this happen on my laptop and this is what cured it for me... In my fstab I changed the drive from /dev/scd0 to /dev/dvd... The problem went away... You may want to try out... /dev/dvd... !!!!BACKUP YOUR FSTAB FIRST!!!!!

Good luck!!

---

### Post by ghantoos on 2007-09-09
> **schickb said:**
> The only icons on my desktop are the names of volumes that have been mounted under /media. That includes the cdrom, two ntfs drives with windows on them, and one ext3 drive with Centos. There are no files under /home/me/Desktop so I have nothing to chown.

The name of the icon on my desktop is "Drivers" becuase that is the CD label  (it actually contains windows drivers). It gets mounted as /media/Drivers, but when ejected that mount point is gone. 

Another interesting point. If I insert a different CD. That new CD appears on my desktop correctly and the old icon continues to exist in a disconnected state. So its always the CD that is in the drive when I first boot that gets stuck there. If I logout and log back in the extra icon goes away. The problem is also fixed if I restart X without rebooting.

Really seems like the problem must be in Gnome with whatever determines which icons to add to the desktop. Thanks for the continued suggestions.

You can try out in a console gconf-editor
browse to apps -> nautilus > desktop
and try to check/uncheck the volumes_visible variable.

cheers,

ghantoos

---

