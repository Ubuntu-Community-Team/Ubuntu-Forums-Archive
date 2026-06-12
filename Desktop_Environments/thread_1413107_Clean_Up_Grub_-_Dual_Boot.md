---
title: "Clean Up Grub - Dual Boot"
date: 2010-02-22
forum: Desktop Environments
---

### Post by jgcallisto on 2010-02-22
I had an ubuntu desktop and have also installed XP on it. I now have the GRUB menu where I can choose installs, but I am a bit embarrassed to say that I had botched things, so had reinstalled ubuntu desktop. My grub menu is now quite crowded, as I have options for the reinstall of ubuntu desktop, xp home, the original ubuntu desktop install (the one I want to keep), and ubuntu server. I'd like to remove the server and the reinstalled deskop environment from the startup menu. Is that possible?  

(The files can stay on the pc. They're not taking up much room, and I may want to play with the server install some day.)

Many thanks!

---

### Post by zvacet on 2010-03-02
In terminal

```
sudo fdisk -l
```

and 

```
cat /etc/fstab
```

post outputs here.

---

### Post by karrank% on 2010-03-04
In Hardy, I go System > Admin > Startup Manager (enter password if prompted) which gets you to various boot options such as number of kernels, default OS, splash screen, theme, etc.

Missed which version you're actually using.

---

### Post by jgcallisto on 2010-03-05
Sorry it took me a couple of days to do this. Here's the info....

I know the desktop installation I want to use is SD6

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d090d09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686   83  Linux
/dev/sda2   *        5100       11473    51199155    7  HPFS/NTFS
/dev/sda3           11474       30400   152031127+  83  Linux
/dev/sda4           30401       60075   238364437+   5  Extended
/dev/sda5           30401       45144   118431117   83  Linux
/dev/sda6           59348       60075     5847628+  82  Linux swap / Solaris
/dev/sda7           45145       45654     4096543+  83  Linux
/dev/sda8           58765       59347     4682916   82  Linux swap / Solaris
/dev/sda9           45655       58764   105306043+  83  Linux

Partition table entries are not in disk order
```And the second one...

```
rangerone@rangerone-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=eeb9b7d9-c63d-4c0c-a533-555b52489887 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0fd5b8f8-3c9f-4b3a-900d-2a0c908352e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
rangerone@rangerone-desktop:~$ 


```Many thanks!

---

### Post by zvacet on 2010-03-05
It look like you have two Ubuntu installations.You didn't reinstall ubuntu desktop witch is package but install Ubuntu again.If your first install was on sda1 and Windows on sda2 then you can delete other partitions if you didn't make separate home.If you want to make separate homwe (I think it is good idea) then read [this.]("http://www.psychocats.net/ubuntu/separatehome")But before you do that you have to reinstall grub.Because i don't know witch version do you use if you use Karmic read [this]("https://help.ubuntu.com/community/Grub2"),and if you use previous version then read [this.]("http://ubuntuforums.org/showthread.php?t=224351")

---

