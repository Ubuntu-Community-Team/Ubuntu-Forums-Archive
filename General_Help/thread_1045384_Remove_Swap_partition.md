---
title: "Remove Swap partition"
date: 2009-01-20
forum: General Help
---

### Post by MadnessRed on 2009-01-20
Hi, I am intending to install Windows 7 beta on my computer how I have a problem I have run out of partitions, I 4 partitions currently, Linux, Swap, XP and DATA. I have un-allocated space to make a partition in but there appears to be a limit, this basically means I have to remove one of my partitions, (or install windows on my data drive which is fat32.

I don't want to remove Windows XP or Linux, so I was wondering is there a way of doing any of the following, order by preference.

1) Trick my hard drive into allowing me a fifth partition.
2) Moving SWAP drive to a usb stick or something like that
3) Remove SWAP partition and have it as a virtual drive.
4) Remove SWAP and use another parition instead as swap as well as its current purpose.
5) Just remove swap all together

Many thanks

Anthony,

ps: I am downloading a partition manager for windows now, will see how that goes.

---

### Post by rug2 on 2009-01-20
After doing what you require, make a new swap partition and then edit /etc/fstab to point out which partition the new swap will be in. 


Take a look at this:
[http://ubuntuforums.org/showthread.php?t=358613](http://ubuntuforums.org/showthread.php?t=358613)

---

### Post by HermanAB on 2009-01-20
You can use a swap file.  This is not any slower than a swap partition.  

See 'man swapon'.

Cheers,

Herman

---

### Post by rug2 on 2009-01-20
> **HermanAB said:**
> You can use a swap file.  This is not any slower than a swap partition.  

See 'man swapon'.

Cheers,

Herman

That's cool.... So you can do this anywhere.. even on a flash drive. Nice. :)

---

### Post by Yellow Pasque on 2009-01-20
4 is probably the best option. Assuming your Linux partition has enough free space, you can create a swapfile in it:
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

Note: If you resize/move partitions, the UUID's will change. Look at /etc/fstab and /boot/grub/menu.lst and realize the implications of this.

Good luck with resizing the partitioinstalling

---

### Post by caljohnsmith on 2009-01-20
It's possible to convert one or more of your primary partitions into logical partition(s) inside of an extended partition, and then you can create as many logical partitions as you want within the extended partition. That way you can keep your swap partition if you want to, but it depends on the physical layout of your partitions as to what options you have, so how about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by MadnessRed on 2009-01-20
hi, thanks for all your suggestions, the swap file is interesting and I will remember that one, however I found out the the 5 partition limit was seomthing that windows made up so when I used a different partition editor it created fine.

Thanks for all the solutions, though, my next question is though, I need to re-apply grub, how do I know what the partition number is for my new Windows partition?

---

### Post by sedawk on 2009-01-20
Installing Windows 7 (into the previous swap partition) will
most likely kill your grub  boot loader.
So you might have to reinstall ("repair") it after booting the LiveCD.
(Or you create a backup of the first 512 bytes of your MBR and
 restore that afterwards also using the LiveCD.)

There are lots of threads here describing how to repair grub

For adding a Windows entry to your menu.lst of grub it might be
sufficient to run 
/usr/sbin/update-grub

---

### Post by MadnessRed on 2009-01-20
> **sedawk said:**
> Installing Windows 7 (into the previous swap partition) will
most likely kill your grub  boot loader.
So you might have to reinstall ("repair") it after booting the LiveCD.
(Or you create a backup of the first 512 bytes of your MBR and
 restore that afterwards also using the LiveCD.)

There are lots of threads here describing how to repair grub

For adding a Windows entry to your menu.lst of grub it might be
sufficient to run 
/usr/sbin/update-grub

Thanks, I know how to repair grub, I have done it many times, the problem I ave is identifying the number of the hard drive so I can add windows 7 to grub

---

### Post by wesley_of_course on 2009-01-21
If you meant the uuid  ; try this  ```
 ls -lf /dev/disk/by-uuid
```  Hope you figure it out and post back .

---

### Post by MadnessRed on 2009-01-25
ok, now I have a problem I went to re-install grub, but...

```
grub> root (hd0,1)

Error 21: Selected disk does not exist
```

This is my partition tables, I think...
> hd0,0 - Windows XP
hd0,1 - Linux Ubuntu
hd0,3 - Linux SWAP
hd0,4 - Windows 7
hd0,5 - DATA

ok, not good, so typed in all the relating commands i could find on the internet.

```
ubuntu@ubuntu:~$ ls -lf /dev/disk/by-uuid
.   2697-0752         db2f79c5-5a1b-4ead-837a-d3ac0a2223d9  DABC6028BC60017D
..  A51DE52DE18BDEFD  177a92e6-11bd-4ec7-9203-27aaea6d7b7c
```

```
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0
```

```
ubuntu@ubuntu:~$ fdisk -l /dev/hda
(-blank-)
```

```
ubuntu@ubuntu:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
tmpfs        tmpfs   1014M   16M  998M   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs        tmpfs   1014M   16M  998M   2% /lib/modules/2.6.24-16-generic/volatile
varrun       tmpfs   1014M  100K 1014M   1% /var/run
varlock      tmpfs   1014M     0 1014M   0% /var/lock
udev         tmpfs   1014M   80K 1014M   1% /dev
devshm       tmpfs   1014M   12K 1014M   1% /dev/shm
tmpfs        tmpfs   1014M   16K 1014M   1% /tmp
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon   1014M   30M  984M   3% /home/ubuntu/.gvfs
/dev/sda5  fuseblk     19G   11G  8.6G  55% /media/Windows
/dev/sda6     vfat    159G   98G   61G  62% /media/DATA
/dev/sda2     ext3     37G   36G   65M 100% /media/disk
/dev/sda1  fuseblk     19G   14G  4.8G  75% /media/disk-1

```

Any ideas? I have reinstalled grub before with no problem.

---

### Post by caljohnsmith on 2009-01-25
How about posting:
```
sudo fdisk -lu
```
Also, when you ran the Grub commands, did you remember to use "sudo grub" and not just "grub"? That is often a cause of Grub returning errors when in the Grub command line.

---

### Post by MadnessRed on 2009-01-25
> **caljohnsmith said:**
> How about posting:
```
sudo fdisk -lu
```
Also, when you ran the Grub commands, did you remember to use "sudo grub" and not just "grub"? That is often a cause of Grub returning errors when in the Grub command line.

ill try sudo grub, and the ls command 1 sec, let me reboot

edit: sudo grub works Thank you so much!!!

---

