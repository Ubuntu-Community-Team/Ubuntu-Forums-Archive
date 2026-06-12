---
title: "Problem Formatting second drive to NTFS"
date: 2009-04-06
forum: General Help
---

### Post by Wired16 on 2009-04-06
I have used GParted and it will not allow me to format to NTFS so i can clean install xp black is there a cmd that will allow me to do this?

---

### Post by kanikilu on 2009-04-06
Is the partition you are trying to format mounted? If so, try unmounting first.

Also, if all you are going to do is install XP, you don't necessarily need to pre-format it...you can format during the install.

---

### Post by JC Cheloven on 2009-04-06
> **Wired16 said:**
> I have used GParted and it will not allow me to format to NTFS so i can clean install xp black is there a cmd that will allow me to do this?

Please give some further details. 
- What are your current partition setup? (sudo fdisk -l)
- Wich partitions were mounted when using gparted?
- ... what are you trying to do? (it seems you're about to delete your current MBR)

---

### Post by Wired16 on 2009-04-06
I am currently trying to install windows xp black. Also I have tried formatting in intsall but it doesn't let me choose the filesystem it just goes to raw for some reason. here are the results of the fdisk -l ```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbabababa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48641   390708801   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a1d3750

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a1d374d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38912   312560608+   7  HPFS/NTFS

```
i am trying to do it on the fat32 one... Neither sdb1 or sdc1 will allow me to install the windows xp on them even though sdc1 has NTFS on it

---

### Post by Wired16 on 2009-04-06
bump

---

### Post by Wired16 on 2009-04-07
Bump

---

### Post by coffeecat on 2009-04-07
Gparted can't create NTFS partitions until you install ntfsprogs.

No, I don't know why ntfsprogs isn't included in a default install either.

---

### Post by Wired16 on 2009-04-07
> **coffeecat said:**
> Gparted can't create NTFS partitions until you install ntfsprogs.

No, I don't know why ntfsprogs isn't included in a default install either.

Ok i installed dtfsprogs and made the drive NTFS but it still is saying it iwsnt windows compatible... bout to say screw it

---

### Post by coffeecat on 2009-04-07
What is saying it isn't Windows compatible?

**Edit:**Just a minute. A quick google tells me Windows Black is a pirated warez version. Is this so? Discussing pirated software is against forum policy.

---

### Post by Wired16 on 2009-04-07
When I boot to the install cd. It brings me to where I select what hard drive to install it in. I have NTFS on my drive and it reads it as NTFS but when I try and install windows it says that it isnt windows compatable. So, idk what is up maybe it is just the cd i have

---

### Post by Elfy on 2009-04-07
Hi

Firstly you don't need to format to run the installer 

Secondly - we don't support pirated software.

---

