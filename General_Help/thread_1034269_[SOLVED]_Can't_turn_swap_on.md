---
title: "[SOLVED] Can't turn swap on"
date: 2009-01-08
forum: General Help
---

### Post by theozzlives on 2009-01-08
I created a 2 GB swap (from my windows) so I can try hibernation. I tried to hibernate and it wouldn't, so I thought I'd check my swap. It was off so I hit swapon and got could not activate swap, swapon:/dev/sda5:cannot allocate memory. You don't have to get real simple with me, just tell me what is wrong so I can fix it. Thank You in advance.

---

### Post by mtausig on 2009-01-08
Am I understanding you right, that you try to use a windows partition as a swap partition in linux? That definitely won't work.

Please post the result of "fdisk /dev/sda -l".

---

### Post by theozzlives on 2009-01-08
I resized my Windows and made a swap with the unused space

ozzie@ozzie-laptop:~$ fdisk /dev/sda -l
Cannot open /dev/sda
ozzie@ozzie-laptop:~$ fdisk -l
Cannot open /dev/sda
ozzie@ozzie-laptop:~$

---

### Post by mtausig on 2009-01-08
Sorry, I forgot to mention, that you need to run fdisk as root: "sudo fdisk -l /dev/sda".

Did you create the partition under linux and make it a swap partition?

---

### Post by theozzlives on 2009-01-08
ozzie@ozzie-laptop:~$ sudo fdisk -l
[sudo] password for ozzie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       15633   115089660   83  Linux
/dev/sda3   *       15634       19196    28619797+   7  HPFS/NTFS
/dev/sda4           19197       19457     2096482+   5  Extended
/dev/sda5           19197       19457     2096451   82  Linux swap / Solaris

---

### Post by theozzlives on 2009-01-08
> **mtausig said:**
> Sorry, I forgot to mention, that you need to run fdisk as root: "sudo fdisk -l /dev/sda".

Did you create the partition under linux and make it a swap partition?

yes, I used gparted on the live CD

---

### Post by mtausig on 2009-01-08
That looks OK. 

Did you actually create the swapspace? If not, do so with "sudo mkswap /dev/sda5"

---

### Post by theozzlives on 2009-01-08
> **theozzlives said:**
> yes, I used gparted on the live CD

I shut down my system and turned it back on. I can turn swap on but still can't hibernate

---

### Post by theozzlives on 2009-01-08
/dev/sda5: Device or resource busy

---

### Post by theozzlives on 2009-01-08
I think it goes into hibernation then pops back out and my system load average is 100%, then slowly goes down.

---

### Post by theozzlives on 2009-01-08
this is a different thread, I'll start a new one

---

### Post by theozzlives on 2009-01-09
Well bummer, I thought this thread was solved. Everytime I re-boot, my swap turns itself off. I now have a 4 GB swap, and the UUID is in the fstab... any ideas. I must add that I originally installed without a swap.

---

### Post by mtausig on 2009-01-09
Please post the content of your /etc/fstab and the output of "ls -l /dev/disk/by-uuid"

---

### Post by theozzlives on 2009-01-09
```
ozzie@ozzie-laptop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-01-09 07:58 93064781-041b-423c-8179-85b6c0312b20 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-01-09 01:57 b37ac976-2337-487e-a1ed-80e7a6edf077 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-09 01:57 bbe88f91-aa3a-4d91-bcab-9d704608421a -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-01-09 01:57 FE3884CD3884867D -> ../../sda3
ozzie@ozzie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
/dev/sda2 /home ext3 nodev,nosuid 0 2
# Windows Partition
/dev/sda3 /windows ntfs 0 0
# /dev/sda5
UUID=351ea5ea-d808-494d-9d40-c067e9dcb59d none            swap    sw              0
# DVD Writer
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ozzie@ozzie-laptop:~$ 

```

---

### Post by theozzlives on 2009-01-09
> **mtausig said:**
> Please post the content of your /etc/fstab and the output of "ls -l /dev/disk/by-uuid"

didn't realize the UUIDs didn't match, I think it's fixed now.

---

