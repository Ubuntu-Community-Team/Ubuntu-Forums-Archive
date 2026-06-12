---
title: "Dual Boot Broblem"
date: 2009-04-10
forum: General Help
---

### Post by gus_zernial on 2009-04-10
I have Kubuntu 9.04 with custom 2.6.28 kernel, running on
software RAID (disks sda and sdb). After getting linux running, 
I installed WinXP on an unused partition on sda (sda3 - see below). 
I then used the Kubuntu CD in rescue mode to change the boot partition back to the correct linux partition, update menu.lst, and reinstall 
grub after updating menu.lst. Now *linux* boots OK (as before),
but when I try to boot WinXP from grub it doesn't find the
correct device. Relevant config data is below.

I suspect I've configured the WinXP entry in menu.lst wrong;
comments appreciated. On a related note, what are the commands 
necessary to identify and correlate linux device partitions with
grub partitions?

Thanks!

%sudo fdisk /dev/sda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   fd  Linux raid autodetect
/dev/sda2            6080       54953   392580405    5  Extended
/dev/sda3           54954       60800    46966027+   7  HPFS/NTFS
/dev/sda5            6080        6322     1951866   82  Linux swap / Solaris
/dev/sda6            6323       54953   390628476   fd  Linux raid autodetect

%cat /boot/grub/device.map
(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb

% cat /boot/grub/menu.lst

.
.
.
## ## End Default Options ##

title           Ubuntu jaunty (development branch), kernel 2.6.28.9r1
root            (hd0,0)                                              
kernel          /vmlinuz-2.6.28.9r1 root=/dev/md1 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M                                                                                                         
initrd          /initrd.img-2.6.28.9r1                                                                    

title           Ubuntu jaunty (development branch), kernel 2.6.28.9r1 (recovery mode)
root            (hd0,0)                                                              
kernel          /vmlinuz-2.6.28.9r1 root=/dev/md1 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd          /initrd.img-2.6.28.9r1                                                               

title           Windows XP
root            (hd0,3)   
makeactive                
chainloader     +1     

.
.
.
(other kernels)

---

### Post by tjwoosta on 2009-04-10
hmm.. i may be way off here but try setting the windows enty in your menu.lst to point to hd0,2 instead of 3

my logic..

hd0,0 = sda1
hd0,1 = sda2
hd0,2 = sda3

---

### Post by gus_zernial on 2009-04-10
You are exactly right!! I guess my problem is I don't
know how to count :)

---

