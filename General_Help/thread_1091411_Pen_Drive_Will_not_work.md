---
title: "Pen Drive Will not work"
date: 2009-03-09
forum: General Help
---

### Post by Dr Pepper44 on 2009-03-09
Hey People.

I have noticed that with Ubuntu 8.10 my Pen Drive will not work, It detects that it has been plugged into my Laptop but it will not let me open it up and view the files that are stored on it.

Can anybody tell me how to make it work?
Or does Ubuntu 8.10 Intepid just not like Pen drives?

Thanks.

---

### Post by albandy on 2009-03-09
I think you've removed directly without selecting remove it safely in windows or without unmounting it in Linux.

---

### Post by kanikilu on 2009-03-09
> **Dr Pepper44 said:**
> Can anybody tell me how to make it work?
Can you plug it in and then post the results of the following commands at a terminal?

```
sudo fdisk -l
dmesg | tail
```

---

### Post by Dr Pepper44 on 2009-03-09
> **kanikilu said:**
> Can you plug it in and then post the results of the following commands at a terminal?

```
sudo fdisk -l
dmesg | tail
```

I have plugged it in and done the commands you told me to, the following text appeared...

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ef08a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         249     2000061    7  HPFS/NTFS
```

**Note:***When I plugged it in, a window appeared saying _"Unable to mount the volume"_*

---

### Post by chen74 on 2009-03-09
maybe you could create a boot disk to enable your pen drive to work. Look on pen drive Linux site and it should explain how to do it. I had the same problem and managed to sort it :O) 





all the best

---

### Post by kanikilu on 2009-03-09
If the flash drive is /dev/sdb1 (2GB), then you could try the following:

1) Create a mount point: ```
sudo mkdir /media/pendrive
```
2) Mount pen drive: ```
sudo mount -t ntfs-3g /dev/sdb1 /media/pendrive -o force
```

If that 2GB partition is something else, then I'm not sure what it could be...can you post the results of **dmesg | tail**?

---

### Post by Dr Pepper44 on 2009-03-09
> **kanikilu said:**
> If the flash drive is /dev/sdb1 (2GB), then you could try the following:

1) Create a mount point: ```
sudo mkdir /media/pendrive
```
2) Mount pen drive: ```
sudo mount -t ntfs-3g /dev/sdb1 /media/pendrive -o force
```

If that 2GB partition is something else, then I'm not sure what it could be...can you post the results of **dmesg | tail**?

Thank you thank you!

What you said worked!, Create a mount point :)
I am very greatful to you, I had stuff on the pendrive which is very important to me :)

Thanks :)

---

