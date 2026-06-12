---
title: "Auto-mount fstab uuid help"
date: 2009-02-22
forum: General Help
---

### Post by timbalisto on 2009-02-22
Here is my current fstab 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=32cccf65-e896-4e7a-8acc-c46b57b0815d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=244de5fa-d65a-48e6-b367-c41306739ef0 none            swap    sw              0       0
```I would like my media partition to auto-mount (show up on desktop) at start-up for Rhythmbox, Drapes, and Nautilus bookmarks.
The partition is called Community Storage, is   /dev/sda3 and the     uuid is 64E5C5544F84B8A7
Could someone please generate a correct fstab for me? Thanks.

---

### Post by taurus on 2009-02-22
What filesystem is that (probably a ntfs from looking at the UUID)?  If it's ntfs, use ntfs-config to configure it.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by timbalisto on 2009-02-22
I've used ntfs config in the past with negative results. I know what I want can be done, I've done it before. I've done a clean install of intrepid from hardy so could I use my old fstab, but I don't know if the way fstab works has changed since hardy.

---

### Post by timbalisto on 2009-02-23
I'm going to assume the way fstab works hasn't changed since Hardy and use a part of my old fstab entry.

---

### Post by timbalisto on 2009-02-23
The new fstab should look like this now, right?
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=32cccf65-e896-4e7a-8acc-c46b57b0815d /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda3
UUID=64E5C5544F84B8A7 /media/Community\040Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0

# /dev/sdb5
UUID=244de5fa-d65a-48e6-b367-c41306739ef0 none            swap    sw              0       0
```

---

### Post by spiderbatdad on 2009-02-23
no expert at fstab, but that looks about right. I believe the defaults give you appropriate permissions. If not look into fmask dmask uid: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

