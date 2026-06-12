---
title: "New kernel not booting"
date: 2008-12-28
forum: Desktop Environments
---

### Post by Chronos6 on 2008-12-28
Hello People!

When Intrepid came out i updated the system, but when booting the new kernel was stopping at a point. I checked recovery mode and saw a lot of text(something about modprobe exit-ed). I tried the old kernel and it was working. I'm using it since. I tried to find a solution, turning off the LAN from Bios, or setting PCI flags did not help. I tried to reinstall the kernel many times, tried many varieties no success.

I dont know where can i find older logs(or logs in general), can somebody help me? 

I've made screenshots:
[http://i43.tinypic.com/25zj6ub.jpg]("http://i43.tinypic.com/25zj6ub.jpg")
[http://i41.tinypic.com/30bz3wi.jpg]("http://i41.tinypic.com/30bz3wi.jpg")
[http://i44.tinypic.com/29bzk7r.jpg]("http://i44.tinypic.com/29bzk7r.jpg")


Thanks,
David

---

### Post by albinootje on 2008-12-28
> **Chronos6 said:**
> 
When Intrepid came out i updated the system, but when booting the new kernel was stopping at a point. I checked recovery mode and saw a lot of text(something about modprobe exit-ed). 
I dont know where can i find older logs(or logs in general), can somebody help me? 


Logfiles are here in /var/log/

There's one error about "attempting to access", which is about the partitioning of your disk(s).
Can you show the output of :
```

uname -a
sudo fdisk -l
sudo lshw -c disk -sanitize
cat /boot/grub/menu.lst

```

---

### Post by Chronos6 on 2008-12-28
Thanks for replying. 
2.6.24-21 is working(and the kernels before this), what are not woking are after this(2.6.27-xx).

acpi_pm_good is for my motherboard, there is a workaround what slows down the system, i've checked and this mb does not have this hardware bug. 

```
Linux ubuntu 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

chronos@ubuntu:~$ sudo fdisk -l
[sudo] password for chronos: 

/dev/sda lemez: 80.0 GB, 80026361856 bájt
255 fej, 63 szektor, 9729 cilinder
Egység: cilinderek 16065 * 512 = 8225280 bájt
Lemezazonosító: 0x00000001

  Eszköz Indítás   Eleje         Vége      Blokkok  Az  Rendszer
/dev/sda1   *           1         127     1020096   83  Linux
/dev/sda2             128        9607    76148100   83  Linux
/dev/sda3            9608        9729      979965   82  Linux lapozó / Solaris

chronos@ubuntu:~$ sudo lshw -c disk -sanitize
  *-disk                  
       description: ATA Disk
       product: ST380011A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.06
       serial: [REMOVED]
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00000001
  *-cdrom:0
       description: CD-R/CD-RW writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=open
  *-cdrom:1
       description: DVD writer
       product: CD/DVDW TS-H552B
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: TS12
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
chronos@ubuntu:~$ cat /boot/grub/menu.lst

default		2
timeout		10


title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=90da0ad8-876e-47b0-9f2c-2b0eacb5bf14 ro quiet splash rootflags=data=writeback  crashkernel=384M-2G:64M@16M,2G-:128M@16M acpi_pm_good pci=routeirq
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=90da0ad8-876e-47b0-9f2c-2b0eacb5bf14 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=90da0ad8-876e-47b0-9f2c-2b0eacb5bf14 ro quiet splash rootflags=data=writeback  crashkernel=384M-2G:64M@16M,2G-:128M@16M acpi_pm_good
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=90da0ad8-876e-47b0-9f2c-2b0eacb5bf14 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet



```

Thanks.

---

### Post by Chronos6 on 2008-12-28
Nobody?

I tried to look in the logs, but it seems that the errors what i get are not logged yet in the boot process.. dont know how to proceed(thats why i'm asking it here on the first place..)

---

### Post by albinootje on 2008-12-28
> **Chronos6 said:**
> Nobody?

I tried to look in the logs, but it seems that the errors what i get are not logged yet in the boot process.. dont know how to proceed(thats why i'm asking it here on the first place..)

File a bug-report at [http://launchpad.net](http://launchpad.net) and ask there.
Higher chance that developers will look at it, and help/fix.

(Don't forget to mention your special kernel boot parameters.)

---

