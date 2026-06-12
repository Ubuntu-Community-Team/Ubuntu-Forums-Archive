---
title: "Reset during format, HDD disappeared"
date: 2009-03-14
forum: General Help
---

### Post by Pharaun on 2009-03-14
Hi guys. Here's my problem:

My windows was messed up, so I re-installed it and it corrupted my grub. I've read some posts about fixing the grub and tried to fix it by re-installing ubuntu through the live cd but only by skipping the system files and installing grub itself. I think I did something wrong, and the installer started formatting my ext3 partition (which my ubuntu was installed) I panicked and pushed the reset button, and when I re-opened ubuntu live cd my ubuntu hard disk wasn't there. It disappeared.

It may have something to do with the sudden reset during format, but I'm not sure. It's so frustrating to be in this situation just because of a simple grub fix. Probably now my ubuntu is damaged and I can't even see the hard disk of it to start a reinstall.

Any advice is appreciated.

---

### Post by taurus on 2009-03-14
If you just want to reinstall GRUB, there is an easier way.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Boot from the LiveCD and open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Pharaun on 2009-03-14
Here it is : 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x716710e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15591558

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14032   112712008+  83  Linux
/dev/sdb2           14033       14593     4506232+   5  Extended
/dev/sdb5           14033       14593     4506201   82  Linux swap / Solaris

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdc5               2       24321   195350368+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-03-14
See if you can mount your Ubuntu, /dev/sdb1, and if there is still anything on it.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdb1 /media/ubuntu
ls -la /media/ubuntu/home/**username**
```
Replace **username** with your login name for Ubuntu.

---

### Post by Pharaun on 2009-03-14
I think there is something wrong. Before this incident when I wrote :

sudo grub
find /boot/grub/stage1

It would say something like (hd0,1) (dont remember the number correctly)
Now it says :
Error 15: File not found

If I am not mistaken this means that it cant reach the ubuntu hard disk which is the 120gb one in the fstab.

---

### Post by Pharaun on 2009-03-14
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ ls -la /media/ubuntu/home/emre
ls: cannot access /media/ubuntu/home/emre: No such file or directory
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-03-14
What's the output of that command from the error message?

```
dmesg | tail
```

---

### Post by Pharaun on 2009-03-14
When I write dmesg the output is very very long I cant even see the starting point of the output. Do you want me to paste all of it?
At the end it says :
[ 2438.227722] VFS: Can't find ext3 filesystem on dev sdb1.

When I write tail it just waits. Nothing happens

Shall I paste the whole output?

---

### Post by taurus on 2009-03-14
What about

```
sudo blkid
```

---

### Post by Pharaun on 2009-03-14
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="7490DA7290DA3A76" TYPE="ntfs" 
/dev/sdb5: UUID="9b7576d5-fc37-448e-af4a-8c53aaa9f799" TYPE="swap" 
/dev/sdc5: UUID="AEC4F0D3C4F09F31" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-03-14
Maybe you can use Testdisk to recover /dev/sdb1 (Ubuntu partition), [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

---

### Post by Pharaun on 2009-03-14
Okay I will try that now. Thank you very much for your time.

---

