---
title: "hidden partition problem"
date: 2009-02-12
forum: General Help
---

### Post by aerek on 2009-02-12
hi, im aerek. 

ive had a tri-boot setup with ubuntu, backtrack3, and windows xp for awhile now.  the backtrack 4 beta was released so i opted to remove bt3 and install the beta.  everything went smoothly, and i can still boot all 3 operating systems, but now all operating systems are seeing one of my partitions as hidden.  here is my setup

first hard drive (sda)
sda1 - has the windows xp operating system (ntfs)
sda2 - this partition is now hidden it is ntfs and contains documents and applications for my windows install

second hard drive (sdb)
sdb1 - ntfs partition
sdb2 - bt4 boot partition
sdb3 - linux swap partition
sdb4 - backtack4 partition

i dont have a partition for ubuntu as ive used wubi to install it

whenever i boot into windows it does not see sda2, using a disk utility (acronis disk director in windows) i can see that the partition is set to hidden.  i tried to change it, but upon reboot it is hidden again.  so i backed up the data on the partition reformatted, deleted then remade the partition and after reboot it is still hidden.

i currently use lilo as my boot loader...could lilo be hiding the sda2 partition on boot?  if so how can i fix this?

---

### Post by uberg on 2009-02-12
When you load windows does it see this partition?

Did you use fdisk -l to get the info for your drives?

---

### Post by aerek on 2009-02-12
no windows does not see the partition, but if i use a disk utilty (like acronis disk director i can see that it is hidden)  here is the output of fdisk

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed8a6ae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1586    12739513+   7  HPFS/NTFS
/dev/sda2            1587        9729    65408647+  17  Hidden HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0c62a775

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      411605   207448888+   7  HPFS/NTFS
/dev/sdb2   *      411606      411736       66024   83  Linux
/dev/sdb3          411737      413818     1049328   82  Linux swap / Solaris
/dev/sdb4          413819      484521    35634312   83  Linux
```

---

### Post by caljohnsmith on 2009-02-12
It's not difficult to unhide a partition, but it sounds like there is something else that hides it when you boot. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your hidden partition problem might be.

---

### Post by aerek on 2009-02-12
ok, i managed to solve the problem with the following:

added the following to the lilo.conf
```
# Override dangerous defaults that rewrite the partition table
change-rules
reset
```

changed the following line in lilo.conf 
```
boot=/dev/sdb
```

to

```
boot=/dev/sda
```

before writing the changes to lilo i used fdisk to change the type of the hidden partition

```
fdisk /dev/sda

t (tells fdisk to change partition type)
2 (to select the hidden partition sda2)
7 (set to ntfs not hidden, was set to 17 which is ntfs hidden)
w (to write the changes)
```

and then wrote the changes to lilo with the following

```
lilo -v
```

after some heavy searching it turns out that lilo sometimes may set a partition to hidden upon booting adding the changes-rules lines to lilo.conf keeps the partition table from being rewritten, so it will keep lilo from hiding it on every boot.  the partition no longer shows up hidden when booting any of the operating systems.  i do appreciate the quick response though

---

