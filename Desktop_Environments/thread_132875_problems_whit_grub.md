---
title: "problems whit grub"
date: 2006-02-19
forum: Desktop Environments
---

### Post by insidious on 2006-02-19
grub says only grub loading please wait but nothing happens! i think i must install the grub agen but i don know how? i use now live-cd. Can some one help me?

---

### Post by heimo on 2006-02-19
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

---

### Post by codejunkie on 2006-02-19
[QUOTE=insidious]grub says only grub loading please wait but nothing happens! i think i must install the grub agen but i don know how? i use now live-cd. Can some one help me?[/QUOTE]
you use this command from the live cd to reinstall grub 
```
sudo grub-install /dev/hda
```if this dosn't work you'll have to do this ```
sudo fdisk -l
```find your ubuntu partition it will look something like this /dev/hdxx replace xx with your drive letter and partition number then 
```
sudo mkdir /mnt/ubuntu
```
```
sudo mount /dev/hdxx /mnt/ubuntu
```
```
sudo chroot /mnt/ubuntu
```
and last
```
sudo grub-install /dev/hda
```

---

### Post by SamTheShaman on 2006-03-28
[QUOTE=codejunkie]you use this command from the live cd to reinstall grub 
```
sudo grub-install /dev/hda
```if this dosn't work you'll have to do this ```
sudo fdisk -l
```find your ubuntu partition it will look something like this /dev/hdxx replace xx with your drive letter and partition number then 
```
sudo mkdir /mnt/ubuntu
```
```
sudo mount /dev/hdxx /mnt/ubuntu
```
```
sudo chroot /mnt/ubuntu
```
and last
```
sudo grub-install /dev/hda
```[/QUOTE]


This is the closest I ever got at least some of what you said worked

Here's what I got
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14313   114969141   83  Linux
/dev/hda2           14314       14596     2273197+   5  Extended
/dev/hda5           14314       14596     2273166   82  Linux swap / Solaris

Disk /dev/hdd: 10.2 GB, 10245537792 bytes
16 heads, 63 sectors/track, 19852 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdd doesn't contain a valid partition table
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu
root@ubuntu:/# sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
/dev/hda: Not found or not a block device.
root@ubuntu:/#


This is my first ever install of linux. I have been working at it for more than a week with no luck. Any idea what I doing wrong.
I get the grub installion failled when I try to install from live CD. From install CD I get a brown screen that jams. Breezy gives me unable to mount CD.

I am at wits end on how to install

](*,)

---

