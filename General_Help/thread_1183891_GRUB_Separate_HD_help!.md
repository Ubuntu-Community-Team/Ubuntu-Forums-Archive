---
title: "GRUB Separate HD help!"
date: 2009-06-10
forum: General Help
---

### Post by Orwhaleca on 2009-06-10
I recently installed Kubuntu on separate hard disk. On my hd0, I have an ubuntu/XP dual-boot. Kubuntu is on my hd2. Is it possible to modify GRUB to boot it?

---

### Post by Entropy_Sam on 2009-06-10
Of course!

Please post the results of **sudo fdisk -l** and **mount**, the contents of /boot/grub/menu.lst and the contents of /boot/grub/device.map so we can tell you what you'll need to add. Also, tell us the linux name of the kubuntu root partition.

If you do that, I should be able to tell you exactly what you need to do.

---

### Post by rCXer on 2009-06-10
[This](http://ubuntuforums.org/showthread.php?t=1181160) thread may help.

---

### Post by dsmithnc on 2009-06-10
> **Entropy_Sam said:**
> Of course!

Please post the results of **sudo fdisk -l** and **mount**, the contents of /boot/grub/menu.lst and the contents of /boot/grub/device.map so we can tell you what you'll need to add. Also, tell us the linux name of the kubuntu root partition.

If you do that, I should be able to tell you exactly what you need to do.

Entoryp_Sam,

I'm not the original poster but have the same question.  Here are the results:

sudo fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40cea6d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x024446e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12240    98317768+   7  HPFS/NTFS
/dev/sdb2           12241       38913   214250872+   f  W95 Ext'd (LBA)
/dev/sdb5           12241       38913   214250841    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x640e2e7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14593   117218241    c  W95 FAT32 (LBA)
/dev/sdc2           14594       14946     2835472+   5  Extended
/dev/sdc5           14594       14780     1502046   83  Linux
/dev/sdc6           14781       14818      305203+  82  Linux swap / Solaris
/dev/sdc7           14819       14946     1028128+  83  Linux

Disk /dev/sdd: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x2e2ec304

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       15288     3913712    b  W95 FAT32

Disk /dev/sde: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders
Units = cylinders of 6550 * 512 = 3353600 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               2        2396     7839744    b  W95 FAT32

mount:

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dick)
/dev/sdc1 on /media/ONETOUCH type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sde1 on /media/TRANSCEND type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd1 on /media/STORE N GO type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc7 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/DRV2_VOL1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/DRV2_VOL2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

menu.lst:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56f07de1-e97f-471f-aa12-8e52f5315c2f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		56f07de1-e97f-471f-aa12-8e52f5315c2f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc



Thanks for your help.

Dick

---

### Post by merlinus on 2009-06-10
If you are trying to run windows, there is no entry for it in menu.lst.

It seems that it in on your second hdd, so adding this at the very end may help:


title  Windows
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

---

### Post by Entropy_Sam on 2009-06-11
Did you want to boot Kubuntu like the OP? If that's the case, which of your multitudinous partitions is the Kubuntu root partition? :-)

---

### Post by dsmithnc on 2009-06-11
> **Entropy_Sam said:**
> Did you want to boot Kubuntu like the OP? If that's the case, which of your multitudinous partitions is the Kubuntu root partition? :-)

Actually, no, just to Ubuntu

Dick

---

### Post by Entropy_Sam on 2009-06-11
If you're trying to dual boot XP and Ubuntu, then user merlinus' suggestion, in your case :-)

---

### Post by dsmithnc on 2009-06-11
> **Entropy_Sam said:**
> If you're trying to dual boot XP and Ubuntu, then user merlinus' suggestion, in your case :-)

Thanks to both you and Merlinus for the suggestions.

Dick

---

### Post by merlinus on 2009-06-11
Glad it is working.  Post back with any other issues.

Happy ubuntuing...

---

### Post by dsmithnc on 2009-06-12
> **merlinus said:**
> Glad it is working.  Post back with any other issues.

Happy ubuntuing...

It is, indeed, working.  I wonder if there is a way to increase the delay b4 Grub loads Ubuntu by default?  I can't be day-dreaming when it flashes up on the screen of I miss getting to the Grub list.

Dick

---

### Post by merlinus on 2009-06-12
```

gksudo gedit /boot/grub/menu.lst

```Find and change the timeout line:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

---

### Post by Orwhaleca on 2009-06-15
Hmm, methinks it best to tell the entire story...
The cd drive on the computer that I was trying to install Kubuntu on was having problems, so I took the hdd that I want Kubuntu on & put it in a separate computer. I installed Kubuntu without a problem. However, when I put the hdd with Kubuntu back in the original computer, I couldn't boot on the 2nd computer. The GRUB reads:
GRUB loading..
Error 17

---

### Post by dsmithnc on 2009-06-16
> **merlinus said:**
> ```

gksudo gedit /boot/grub/menu.lst

```Find and change the timeout line:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

Merlin,

Thanks again for all your help.  Folks like you make the transition to Ubuntu much, much easier.

Dick

---

