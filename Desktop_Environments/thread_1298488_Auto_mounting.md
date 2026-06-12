---
title: "Auto mounting"
date: 2009-10-22
forum: Desktop Environments
---

### Post by dfreehill on 2009-10-22
Hi all,

I have a second drive in my computer that I use to share files with Windows computers, It's formated as fat32. As it is now I have to click on it to mount it so that the shares are seen on the network. I would like to auto mount it on bootup, I know I've done this before but don't remember how can someone help me.

TIA!
Dan

---

### Post by undecim on 2009-10-22
put a new line in /etc/fstab. Something like:
```
/dev/sdb1 /media/disk vfat defaults 0 0
```

where /dev/sdb1 is the device (seen from df when mounted) /media/disk is where you want it to mount.

Instead of the device name, you can also use UUID, which won't change, even if the /dev/sdx1 device changed (i.e. you have two external drives plugged in) you can find it with the command "ls -l /dev/disk/by-uuid/", and in place of /dev/sdb1 use "UUID=id" where id is the UUID of the disk

Or you can also use "LABEL=name" where  name is the name/label of the disk (usually, the folder under /media/ where is mounted, unless it mounts to /media/disk)

---

### Post by chris.reid on 2009-10-22
You can also use the following to get the UUID
```
blkid
``` or 
```
vol_id /dev/xxxx
```The nice thing about blkid is that it gives you the drive, UUID, TYPE everything you need for the fstab.

if using the UUID your fstab will contain the lines in this format :
```

UUID=879e053a-0253-4817-b0e9-4e4f94f21f82    /media/linuxData    ext3 
UUID=D814-41E3                    /media/fatData        vfat    
//192.168.1.100/_SOFTWARE        /media/black/software    smbfs    

```

---

### Post by dfreehill on 2009-10-22
Thank you chris.reid and undecim.

---

