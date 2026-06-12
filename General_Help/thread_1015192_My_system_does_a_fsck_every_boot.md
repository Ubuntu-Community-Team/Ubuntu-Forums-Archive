---
title: "My system does a fsck every boot"
date: 2008-12-18
forum: General Help
---

### Post by BetterSense on 2008-12-18
When I boot my desktop, it hangs forever on what I believe is a fsck. It says something about fsck (march 2008) and then 

```
Reiserfs journal '/dev/sda2' in blocks [18..8211]: 0 transactions replayed 
```

then it says filesystem is clean. I have a 1TB hard drive, and this takes forever. Isn't it supposed to only check the filesystem every ten times or something?

---

### Post by taurus on 2008-12-18
Can you post your /etc/fstab?

```
cat /etc/fstab
```

---

### Post by BetterSense on 2008-12-18
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3c1c9d25-94fa-4dd8-9c34-92744bbe6ae9 /               ext3    errors=remount-ro 0       1
# /dev/sda2
UUID=9b097222-9924-4932-a91b-169c95f8e53e /home           reiserfs defaults        0       2
                /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# For USB access with Virtualbox
none    /proc/bus/usb   usbfs   devgid=1002,devmode=664 0       0

```

---

### Post by LateNiteTV on 2008-12-19
y do u have different file systems for / and /home?

---

### Post by dcstar on 2008-12-19
> **BetterSense said:**
> When I boot my desktop, it hangs forever on what I believe is a fsck. It says something about fsck (march 2008) and then 

```
Reiserfs journal '/dev/sda2' in blocks [18..8211]: 0 transactions replayed 
```

then it says filesystem is clean. I have a 1TB hard drive, and this takes forever. Isn't it supposed to only check the filesystem every ten times or something?

Reiserfs will always do a fsck if you have the "2" set in fstab, EXT2 allows you to set the fsck to various counts/dates.

---

### Post by BetterSense on 2008-12-19
> **LateNiteTV said:**
> y do u have different file systems for / and /home?

I was experimenting with Reiser. I didn't want to experiment with using it on /, and I didn't think it was even bootable IIRC. This was a long time ago.

> Reiserfs will always do a fsck if you have the "2" set in fstab, EXT2 allows you to set the fsck to various counts/dates. 

What should I set it to? I can leave it really, I don't boot that much.

---

