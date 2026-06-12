---
title: "dual boot doesn't work"
date: 2008-08-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bro on 2008-08-20
Hi, I just bought a Dell xps m1330 laptop. It is not available with ubuntu in my country so I got it with vista. 

I installed ubuntu but messed up Vista.

It had a lot of partitions already. One for 'media direct' (or what its called = get in media without booting) One for 'recovery', one for the OS (vista) and one at the end that I don't what is was for.
Like so: 
| media direct | recovery | vista | ? |

I deleted the recovery, resized vista en moved it to the left, deleted the '?' and made a new extended with '/', '/home', 'swap' and installed ubuntu accordingly. Ofcourse, vista doesn't boot anymore. Neither does the 'media direct' or what its called. 

What to do? Reinstall vista from reinstall dvd?

---

### Post by falcon61102 on 2008-08-21
Just to help make things a little more clear, could you boot up from your Ubuntu CD and start up a Terminal.  Then run and post the results of this command:
```
sudo fdisk -l
```
-l being a lowercase L

---

### Post by bro on 2008-08-21
The output by the way seems to be the same as without the live-cd (I can boot into Ubuntu, just not in Vista) 


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2            7806       38913   249875010    5  Extended
/dev/sda3   *          16        7805    62573175    7  HPFS/NTFS
/dev/sda5            7806       11725    31487368+  83  Linux
/dev/sda6           11726       37282   205286571   83  Linux
/dev/sda7           37283       38913    13100976   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by lackoblacko on 2008-08-21
sounds like your menu.lst might be setup incorrectly.  post your menu.lst as well located at /boot/grub.

---

### Post by bro on 2008-08-21
The last bit of my grup menu.lst
```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=12e97361-f5c4-45e8-9347-c6ad83cd2e38 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=12e97361-f5c4-45e8-9347-c6ad83cd2e38 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

---

### Post by caljohnsmith on 2008-08-21
Something looks strange about your partitioning, because according to fdisk your sda2 is the extended partition containing your linux partitions sda5, sda6 and sda7. And then it shows sda3 as your Vista partition, when really your Vista partition comes after the "Dell utility" partition. 

Try doing the following in a terminal:
```
sudo grub
grub> geometry (hd0)
```
And post the output. Also, reboot your computer, select the "Windows Vista/Longhorn (loader)" in the Grub menu (but don't hit enter), hit "e" to edit it, and then change the "root (hd0,2)" to "root (hd0,1)", and then hit "b" to boot it (it gives you directions, just follow them). See if that works.

---

### Post by bro on 2008-08-21
For your information/interest I posted the outcome below. I solved my problem however by just reinstalling windows followed by reinstalling grub. This only didn't fix the 'dell media direct' which is supposed reside on the first small partition. However it needs to partition and install itself then the windows or it can't be installed. So be it, with a laptop that boots under 40sec I don't see much need for doing it all over again so I can do 'media direct' ;)

Thanx all for thinking along. In the end I just had to do an bit more thinking before I started it. 

```
grub> geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type is fat, partition type 0x6
   Partition num: 2,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type unknown, partition type 0x82

```

---

### Post by TimDaniels on 2008-08-21
> **bro said:**
> Hi, I just bought a Dell xps m1330 laptop. It is not available with ubuntu in my country so I got it with vista. 

I installed ubuntu but messed up Vista.

It had a lot of partitions already. One for 'media direct' (or what its called = get in media without booting) One for 'recovery', one for the OS (vista) and one at the end that I don't what is was for.
Like so: 
| media direct | recovery | vista | ? |

I deleted the recovery, resized vista en moved it to the left, deleted the '?' and made a new extended with '/', '/home', 'swap' and installed ubuntu accordingly. Ofcourse, vista doesn't boot anymore. Neither does the 'media direct' or what its called. 

What to do? Reinstall vista from reinstall dvd?

In the process of shifting the Vista installation "left", you would have invalidated some entries in Vista's BCD.  You can correct that by running the Recovery Environment (in the installation DVD), and using the Command Prompt, run "bootrec /rebuildbcd".  See 
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us) .

Your partitioning has changed since February 2008 when I got _my_ M1330.  In my M1330, the order of the partitions was |utilities|recovery|Vista|MediaDirect, and MediaDirect was a Dell proprietary partition within an Extended partition that was formatted under Vista's new formatting rules, i.e. with a 2,048-sector offset from the beginning of the Extended partition.  If you had tried to add logical partitions to the MediaDirect partition within the Extended partition using Gparted or other non-Vista partition manager, you would have run into problems.  See [http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html).

  Since you should have received the Dell diagnostic utilities on a CD, and you already have a Vista re-installation DVD, and MediaDirect can also be accessed from Vista, the conservative thing to do would be to just clone the Vista installation to an external HD, then delete all non-Vista partitions, create a new Primary partition for Vista using Gparted, then copy the clone back to the new Primary partition and run "bootrec /rebuildbcd" to fix Vista's BCD.  That is what I did, and the subsequent installation of Ubuntu was very easy.  Not so easy was enabling the Vista boot manager to conrol the booting of both OSes, but that's a Vista topic.  :-)

*TimDaniels*

---

