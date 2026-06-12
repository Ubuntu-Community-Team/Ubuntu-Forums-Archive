---
title: "problem in installing ubuntu and win7"
date: 2011-03-07
forum: Desktop Environments
---

### Post by keimasi on 2011-03-07
Hi to all friends
I just install ubuntu 10.10 on my laptop and after that my 7 OS never boot at all.

(I before used linux with vmware on win7)

any way... my friends say it related grub2. 
I use this command :
```

update grub-2

```

but my problem didnt solved.
Please guide me if its possible...

Thanks..

---

### Post by 3Miro on 2011-03-07
Is windows still there at all?

Go to the terminal and type:
```
sudo fdisk -l
```
then post the result here. This will give us the layout of your HDD.

---

### Post by keimasi on 2011-03-07
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000bbc42 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1          13      102400    7  HPFS/NTFS 
Partition 1 does not end on cylinder boundary. 
/dev/sda2              13       12762   102400000    7  HPFS/NTFS 
/dev/sda3           12762       31884   153600000    7  HPFS/NTFS 
/dev/sda4           31884       60454   229490689    5  Extended 
/dev/sda5           31884       37963    48827392   83  Linux 
/dev/sda6           37963       41610    29295616   83  Linux 
/dev/sda7           41610       47689    48827392   83  Linux 
/dev/sda8           47689       50120    19529728   83  Linux 
/dev/sda9           50120       52552    19529728   83  Linux 
/dev/sda10          52552       54375    14647296   83  Linux 
/dev/sda11          54376       56199    14647296   83  Linux 
/dev/sda12          56199       58023    14647296   83  Linux 
/dev/sda13          58023       59239     9764864   83  Linux 
/dev/sda14          59239       60454     9764864   82  Linux swap / Solaris 

```

---

### Post by 3Miro on 2011-03-07
Other than the fact that you have like 10 Linux partitions, everything seems to be working. Try the grub command again

```
sudo update-grub
```

and post the result here.

---

### Post by keimasi on 2011-03-07
Thanks for ur answer
I just repair bootloder by my win7 DVD.
I help this link:
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

