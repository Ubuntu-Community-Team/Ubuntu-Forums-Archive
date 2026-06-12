---
title: "Need to add windows to grub"
date: 2006-08-15
forum: Desktop Environments
---

### Post by archer75 on 2006-08-15
The install didn't add windows to grub. How do I go about adding it? I searched help in the OS for boot manager and it does come up and show me the app to use but that app isn't where it says it should be.

---

### Post by fakie_flip on 2006-08-15
what is the output of this command?
```
sudo fdisk -l
```

---

### Post by archer75 on 2006-08-15
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9039    72605736    7  HPFS/NTFS

Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        7169    57584961   83  Linux
/dev/hdc2            7170        7476     2465977+   5  Extended
/dev/hdc5            7170        7476     2465946   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312576673+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60802   488392033+   7  HPFS/NTFS

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sde doesn't contain a valid partition table

Windows is on the first 74.3gb drive.

I also need to setup NTFS read support of my raid arrays. Those 2 250gb drives are in a Raid 0 and those 2 160gb drives are in a Raid 0.

---

### Post by fakie_flip on 2006-08-15
If windows is installed on /dev/hda1 then you will need to give these commands. If windows is installed somewhere else, change the numbers here (hd0,0) and do all the same commands.
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup # create a backup of your orginal before editing the file
echo "title		Microsoft Windows XP Professional" | sudo tee -a echo echo "/boot/grub/menu.lst
echo "root		(hd0,0)" | sudo tee -a /boot/grub/menu.lst
echo "savedefault" | sudo tee -a /boot/grub/menu.lst
echo "makeactive" | sudo tee -a /boot/grub/menu.lst
echo "chainloader	+1" | sudo tee -a /boot/grub/menu.lst
```

---

### Post by fakie_flip on 2006-08-15
By looking at the output of "sudo fdisk -l", I see that you need to do these commands.

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup # create a backup of your orginal before editing the file
echo "title		Microsoft Windows XP Professional" | sudo tee -a echo echo "/boot/grub/menu.lst
echo "root		(sd0,0)" | sudo tee -a /boot/grub/menu.lst
echo "savedefault" | sudo tee -a /boot/grub/menu.lst
echo "makeactive" | sudo tee -a /boot/grub/menu.lst
echo "chainloader	+1" | sudo tee -a /boot/grub/menu.lst
```[/QUOTE]

---

### Post by archer75 on 2006-08-15
This is what I get when attempting to boot into windows:

Error 13: Invalid or unsupported executable format

---

### Post by fakie_flip on 2006-08-15
These could probably help you.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by fakie_flip on 2006-08-15
I didn't realize you were using serial ata drives. Change (hd0,0) to (sd0,0) in /boot/grub/menu.lst if you did the first set of commands I gave you.

---

