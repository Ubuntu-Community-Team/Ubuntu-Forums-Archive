---
title: "hd options locked?"
date: 2009-02-24
forum: General Help
---

### Post by tranceponderer on 2009-02-24
I have a dual boot set up with xp & ubuntu.
I created a small fat32 partition (using the ubuntu installer) for sharing between the two when I installed ubuntu on top of xp.
I changed the mount location of this partition for easier access later on
-----------------------fstab-----------------------
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=32fa6020-56db-4902-b777-7ca46602c61c /               ext3    relatime,errors=remoun$
# /dev/sda8
UUID=bf4493a5-2860-416f-9ef1-78f0a2af6b56 /boot           ext3    relatime        0     $
# /dev/sda6
UUID=e1bf7da3-af50-4642-9098-9c011f3f4e1a none            swap    sw              0     $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#small#
/dev/sdb1       /home/sunroom/small     ext3    defaults        0       0
#large#
/dev/sdc1       /home/sunroom/large     ext3    defaults        0       0
[COLOR="Red"]#share#
/dev/sda7       /home/sunroom/share     vfat    defaults        0       0
[/COLOR]
***there used to be a UUID entry for this partition ***

It worked fine at first but (i think) after booting into windows the first time after that I no longer have the privileges to wright to that partition from ubuntu.
I can chmod and chown it all I want but nothing will change, I've even tried changing the priveleges with a right click from a sudo nautilus, it will immediately change back to read only 
I get this error message when I try to share the folder in sudo nautilus

Nautilus-Share-Message: unknown format for key 'share/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only


In windows this partition is drive F: 
/share was the original folder it was mounted to
I'm stuck 
Anybody know what i need to do ?

---

### Post by dcstar on 2009-02-24
> **tranceponderer said:**
> I have a dual boot set up with xp & ubuntu.
I created a small fat32 partition (using the ubuntu installer) for sharing between the two when I installed ubuntu on top of xp.
I changed the mount location of this partition for easier access later on
........
Nautilus-Share-Message: unknown format for key 'share/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only


In windows this partition is drive F: 
/share was the original folder it was mounted to
I'm stuck 
Anybody know what i need to do ?

Make the share folder writeable by root.

---

### Post by tranceponderer on 2009-02-25
my problem is that i cant change any of the permissions.
There's something thats auto-restoring the permissions whenever I try to change them.

---

### Post by gleble on 2009-05-03
Exactly my problem. Did you ever solve it?

---

