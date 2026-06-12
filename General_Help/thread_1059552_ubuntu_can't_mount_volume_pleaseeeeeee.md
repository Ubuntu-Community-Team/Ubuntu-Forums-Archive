---
title: "ubuntu can't mount volume pleaseeeeeee"
date: 2009-02-03
forum: General Help
---

### Post by eAi-T0ky0 on 2009-02-03
Hey guys , I have installed ubuntu for year now and it works fine Then I have install "windows" in NTFS partition and grub with it with linux , and it works fine and all my computer partitions works in windows and linux BUT when I update my sources list!! I don't know what happen! When try open my partitions it give me a error that i [COLOR="Red"]can't mount volume[/COLOR] , This is the output for "sudo fdisk -l" 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac91ac91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1307    10498446   83  Linux
/dev/sda2            1308       13932   101410312+   f  W95 Ext'd (LBA)
/dev/sda3   *       13933       19457    44379562+   7  HPFS/NTFS
/dev/sda5            1308        1438     1052226   82  Linux swap / Solaris
/dev/sda6            1439        7685    50178996    7  HPFS/NTFS
/dev/sda7            7686       13932    50178996    7  HPFS/NTFS
```

any one can help please?

---

### Post by Crafty Kisses on 2009-02-03
What are the results of this command?
```
sudo nano /etc/fstab
```

---

