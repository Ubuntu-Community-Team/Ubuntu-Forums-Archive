---
title: "Recovering ubuntu data from a live cd"
date: 2009-04-08
forum: General Help
---

### Post by Sedatcom4 on 2009-04-08
Hey guys,
 My Ubuntu has had an Xserver error and I've tried various things, but nothing works so I decided to create a live cd and just burn the data I had and reinstall Ubuntu. I'm wondering how to do this. I already made a live cd from the iso, but I don't know how to retrieve the data in live mode. Please help! Thanks.

---

### Post by taurus on 2009-04-08
You need to mount the partition where /home is.  If you only have two partitions, / & swap, then you need to mount /.  But if you have a separate /home partition, then you need to mount that partition first before you can access your personal files on $HOME. 

From the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by benj1 on 2009-04-08
firstly its just a case of mounting you hard drive (if it doesn't mount automatically) 
second if you want to burn it to a cd youll need a second cd drive.
If you don't, either a usb drive and then just drag and drop the files you want to save, or get puppy linux and then load it in to ram (its an option when you boot), then you can eject the cd, and put one in for burning.

---

### Post by Sedatcom4 on 2009-04-08
This is the output from 

```
sudo fdisk -l
```

```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2c5540c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c4b9c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3357    26965071    7  HPFS/NTFS
/dev/sdb2            3358        9732    51207187+   f  W95 Ext'd (LBA)
/dev/sdb5            3358        8719    43070233+   7  HPFS/NTFS
/dev/sdb6            8720        9732     8136891    7  HPFS/NTFS

Disk /dev/sdc: 1048 MB, 1048576000 bytes
33 heads, 63 sectors/track, 985 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         986     1023984    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(247, 32, 63) logical=(985, 2, 59)

```

Also, I have no idea how to mount a drive on linux. Ubuntu is installed on the first partition anyway so I don't know what to do.

---

### Post by benj1 on 2009-04-08
> 
Also, I have no idea how to mount a drive on linux. Ubuntu is installed on the first partition anyway so I don't know what to do.

if you go to places you should see a list of hard drives one per partitin labelled 'X.X GB Media' just click on the one matching your ubuntu partition size and it will mount and open in nautilus.

---

### Post by taurus on 2009-04-08
Where did you install Ubuntu anyway because most of them are ntfs filesystems with one fat32/vfat?

Did you install Ubuntu on it own partition or did you install it through windows--wubi?

---

### Post by Sedatcom4 on 2009-04-08
I installed ubuntu through windows. I dled it straight from the ubuntu website, but I don't remember what format it was, as I didn't know how to use iso's then.

The fat32 is the flash drive I have plugged in I think.

---

