---
title: "No Swap File being shown in Ubuntu"
date: 2009-04-06
forum: General Help
---

### Post by tigshadorakie on 2009-04-06
Ubuntu isn't showing that I am using a Swap File. It shows 0 of 0 used in the system monitor. When installing I originally had a swap file but had to use Parted Magic to erase the partition and create a new one. In Parted Magic I gave myself 5 gig of Linux Swap. I have the space available for it but Ubuntu doesn't know it is there to use. Is there a way to point Ubuntu at that partition and have it use that space that I made for it?

---

### Post by anaconda on 2009-04-06
Well.. I didn't quite understand do you now have a swap file or a swap partition?

anyway.

if you have a swap file you can try to run 
swapon /path/to/the/swapfile

The swapon command should also work with a swap partition.
eg.
swapon /dev/sdaXX
You just need to change the sdaXX to the correct swap-partition.

If the swapon command didn't work then you need to format the file/partition to swap. And for that you can use:
mkswap /dev/sdaXX
or
mkswap /path/to/the/swapfile

After that the swapon command should work.

PS. Just thought that your problem is propably that you have re-formatted your swap when you re-made it with "parted magic" And when you reformat a partition the uuid of that partition changes, and the line you have in fstab (for mounting the swap) has still the old uuid, and so swap partition wont be mounted.

Just change the uuid to be the correct one.

PSS. You can check if you have swap enabled with the command "free" (in terminal...)

---

### Post by tigshadorakie on 2009-04-06
Yes I think that is what happened. I have Windows XP on another hdd and I am dual booting Ubuntu. When I used the Ubuntu installer I manaully set everything up and I made the Swap File a Logical or Extended Partition. For some reason Windows was seeing this drive and I didn't want that. So I went back deleted the part and made a new one and formated it as a Linux Swap. I am going to try this real quick. Will post back in a few minutes.

---

### Post by tigshadorakie on 2009-04-06
No, It didn't work. Im not sure what I am doing wrong. Do you mind helping me out a bit more?

---

### Post by kpkeerthi on 2009-04-06
Post the output of ```
sudo fdisk -l
```

---

### Post by tigshadorakie on 2009-04-06
> **kpkeerthi said:**
> Post the output of ```
sudo fdisk -l
```

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9e94641

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           18359       30515    97651102+   7  HPFS/NTFS
/dev/sda2               1       17629   141604911   83  Linux
/dev/sda3           17630       18358     5855692+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7c7d7c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS
chris@Ubuntu:~$

---

### Post by tigshadorakie on 2009-04-06
blkid
/dev/sda1: UUID="7F4BB20312F62F72" TYPE="ntfs" 
/dev/sdb1: UUID="9638DF6138DF3F45" LABEL="XP" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="b7e0cc9b-30d7-41d5-871c-2d49b7fee06f" TYPE="ext3" 
/dev/sda5: UUID="13469f4e-73a2-416a-a056-a49aeebff0c9" TYPE="swap" 
/dev/sda3: TYPE="swap" UUID="fb736ea5-ec8b-4a27-baac-02ce0cf466f7" 

--------------------------
What has my confused is the fact that I am showing an sda5 when I dont know if I really have one.

---

### Post by kpkeerthi on 2009-04-06
Your swap partition is /dev/sda3

So you would run
```
sudo swapon /dev/sda3
```to make this active.

Now check if it is being used using the 'free' command.

---

### Post by kpkeerthi on 2009-04-06
To make the changes permanent, update /etc/fstab
```

/dev/sda3       swap            swap         defaults                0 0

```

Note: You may want to using UUID instead of partition name in FSTAB.

---

### Post by tigshadorakie on 2009-04-06
> **kpkeerthi said:**
> Your swap partition is /dev/sda3

So you would run
```
sudo swapon /dev/sda3
```to make this active.

Now check if it is being used using the 'free' command.

I see it in my system monitor now. It isn't using any swap at the moment though but now shows 0 out of 5 Gig.

I had to also copy and past the new ID for the partition. 

I think I may have neglected to use Sudo before the swapon because when I used that command things seemed to slow down a little and do nothing. 

Thanks for your help.

---

### Post by tigshadorakie on 2009-04-06
Do any of you happen to know of a program that will stress test memory? I know Windows has a lot of them.

---

### Post by kpkeerthi on 2009-04-06
memtest86. Run this tool using Ubuntu Live CD (from the boot menu)

---

### Post by tigshadorakie on 2009-04-06
> **kpkeerthi said:**
> memtest86. Run this tool using Ubuntu Live CD (from the boot menu)

I was thinking of something more along the lines of Orthos that crunches numbers and does complex math calculations.

---

