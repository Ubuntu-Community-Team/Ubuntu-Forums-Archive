---
title: "Major problem!"
date: 2009-06-21
forum: General Help
---

### Post by moster on 2009-06-21
I cannot see my other partition after installing Ubuntu from scratch.

I will explain everything now. Windows is on one HDD Ubuntu on another. Boot and grub working perfectly. Now, on disk that I have linux I have two partitions, one for Ubuntu and one for data. That data partition I mounted as /data in ubuntu instalation an now I cannot see it. Windows partition I see perfectly.

here is post of my fdisk ```

moster@moster-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffbbffbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4864    28828642+   f  W95 Ext'd (LBA)
/dev/sda5            1276        4864    28828611    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d4f4356

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2575    20683656   83  Linux
/dev/sdb2            2576       30401   223512345   83  Linux
moster@moster-desktop:~$ gksu gedit /etc/fstab
```

and fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=45af080e-c43b-4032-ad16-74d6da086023 /               ext4    relatime,errors=remount-ro 0       1
# /data was on /dev/sdb2 during installation
UUID=07d5591d-b76e-4c61-aea2-4ed5cde3b536 /data           ext3    relatime        0       2
```

I do not even see **sdb2** partition in nautilus. But gparted say it is mounted.

---

### Post by Legace on 2009-06-21
Post output of **blkid**

---

### Post by KeyserSoze93 on 2009-06-21
> **Legace said:**
> Post output of **blkid**
**sudo** blkid

---

### Post by moster on 2009-06-21
Ok, sorry for delay, here it is... I forgot to say UUID is good.

```
moster@moster-desktop:~$ sudo blkid
[sudo] password for moster: 
/dev/sda1: UUID="40C43318C4330FA0" LABEL="win" TYPE="ntfs" 
/dev/sda5: UUID="BA34BDFA34BDB9A9" LABEL="windata" TYPE="ntfs" 
/dev/sdb1: UUID="45af080e-c43b-4032-ad16-74d6da086023" TYPE="ext4" 
/dev/sdb2: LABEL="data" UUID="07d5591d-b76e-4c61-aea2-4ed5cde3b536" TYPE="ext3" SEC_TYPE="ext2" 
moster@moster-desktop:~$ 

```

---

### Post by coffeecat on 2009-06-21
> **moster said:**
> I do not even see **sdb2** partition in nautilus.

What exactly do you mean? Is it that it is not showing up in the Places menu, or in the left pane of a Nautilus window? What happens if you go to Places > Computer > Filesystem ? Does /data appear between /cdrom and /dev? Can you navigate into it?

---

### Post by moster on 2009-06-21
> **coffeecat said:**
> What exactly do you mean? Is it that it is not showing up in the Places menu, or in the left pane of a Nautilus window? What happens if you go to Places > Computer > Filesystem ? Does /data appear between /cdrom and /dev? Can you navigate into it?

**YES!** I see it. hm, what happend, and how do I get it to mount in proper way? Please :)

---

### Post by coffeecat on 2009-06-21
> **moster said:**
> **YES!** I see it. hm, what happend, and how do I get it to mount in proper way? Please :)

What do you mean by "in the proper way"? It is being mounted if you can navigate into it from Computer. You need to give more information. Can you see it in Places? Do you mean that you want a desktop icon?

**Edit:** to clarify - it is not enough if you can simply "see" /data. /data is simply the mountpoint. Did you double-click on it? Is there anything visible when you do?

---

### Post by moster on 2009-06-21
> **coffeecat said:**
> What do you mean by "in the proper way"? It is being mounted if you can navigate into it from Computer. You need to give more information. Can you see it in Places? Do you mean that you want a desktop icon?

**Edit:** to clarify - it is not enough if you can simply "see" /data. /data is simply the mountpoint. Did you double-click on it? Is there anything visible when you do?

OMG. Ok.. I now know what happened...

That partition was mounted directly on /data. And nautilus was not see it as mount point. I changed fstab to /media/data and everything is OK now.

hehe, little stupid but I almost **** myself because it was my primary partition and no backup was made :)

Thanks for help :)

---

