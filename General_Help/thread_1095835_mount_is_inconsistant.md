---
title: "mount is inconsistant"
date: 2009-03-14
forum: General Help
---

### Post by lian1238 on 2009-03-14
Hi all,

I've had this problem since Hardy, and have found no explanation. I have 6 separate partitions for the following directories:

[LIST]
[*]/
[*]/home
[*]~/Pictures
[*]~/Music
[*]~/XP
[*]~/VM
[/LIST]
Before Hardy, they didn't show up in My Computer as volume, which was good. I chose to show mounted volumes on the desktop, so my USB drives would show on the desktop. Also comes Hardy, and I did a fresh install on my root directory, leaving the other partitions untouched. Then, I edited the fstab to look like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=38d8011f-0329-4164-aee8-1a3634a98f8a /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda6
# UUID=48fa399f-23c3-4364-bced-83bc14107516 /home           ext3    relatime        0       2
/dev/sda6 /home ext3 nodev,nosuid 0 2

# /dev/sda7
/dev/sda7 /home/lian/Music ext3 nodev,nosuid 0 2
# UUID=355e3d3f-ad57-4354-81ad-db71e39a212b /home/lian/Music ext3    relatime        0       2

# /dev/sda5
/dev/sda5 /home/lian/Pictures ext3 nodev,nosuid 0 2
# UUID=9f1eddce-8786-4999-b0ea-3d6bfc373617 /home/lian/Pictures ext3    relatime        0       2

# /dev/sda8
/dev/sda8 /home/lian/VM ext2 nodev,nosuid 0 2
# UUID=06b14940-dc26-4f31-a34f-bb6bdbc51204 /home/lian/VM   ext2    relatime        0       2

# /dev/sda1
/dev/sda1 /home/lian/XP/ ext3 nodev,nosuid 0 2
# UUID=ef3811f9-9bae-4cad-92aa-cb338074fc49 /home/lian/XP   ext3    relatime        0       2

# /dev/sda10
UUID=ea380ab0-ec78-4376-897b-948cd8cc318d none            swap    sw              0       0

/dev/scd0       /media/cdrom0  udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

# work around USB not auto-mounted.. :(
/dev/sdb1 /media/sdb1 vfat user 0 0
/dev/sdc1 /media/sdc1 vfat user 0 0
/dev/sdd1 /media/sdd1 vfat user 0 0
/dev/sde1 /media/sde1 vfat user 0 0

```

The commented lines are the old ones I no longer use. (I don't know what is UUID). The problem is they all except /home show up as drives in My Computer. I do NOT want this.. It makes a mess on my desktop when I show mounted drives.

I still have hope for this, because it used to be the way I like it before Hardy. Any help is appreciated!

---

### Post by heindsight on 2009-03-14
In Hardy all file systems mounted under your home directory will show up on your desktop if you have the option to show mounted volumes on the desktop enabled.

If you do not want to see these filesystems on your desktop, I'd suggest mounting them somewhere else (perhaps at /mnt/Pictures, /mnt/Music,  /mnt/XP and /mnt/VM) and then replace the corresponding directories in your home with symbolic links to the mount points. Eg:
```
ln -sf /mnt/Pictures /home/lian/Pictures
```

EDIT:
I have 2 partitions mounted at
/home/heindsight/media and /home/heindsight/work
Having them show up on my desktop used to irritate me quite a bit too. Especially since they showed up as '56GB Media' and '2GB Media', until I changed their filesystem labels to Media and Work and now they show up as 'Media' and 'Work' on my desktop and I rather like it...

---

### Post by lian1238 on 2009-03-14
> **heindsight said:**
> In Hardy all file systems mounted under your home directory will show up on your desktop if you have the option to show mounted volumes on the desktop enabled.

If you do not want to see these filesystems on your desktop, I'd suggest mounting them somewhere else (perhaps at /mnt/Pictures, /mnt/Music,  /mnt/XP and /mnt/VM) and then replace the corresponding directories in your home with symbolic links to the mount points. Eg:
```
ln -sf /mnt/Pictures /home/lian/Pictures
```EDIT:
I have 2 partitions mounted at
/home/heindsight/media and /home/heindsight/work
Having them show up on my desktop used to irritate me quite a bit too. Especially since they showed up as '56GB Media' and '2GB Media', until I changed their filesystem labels to Media and Work and now they show up as 'Media' and 'Work' on my desktop and I rather like it...

That did it, **heindsight**. Thanks so much!

---

