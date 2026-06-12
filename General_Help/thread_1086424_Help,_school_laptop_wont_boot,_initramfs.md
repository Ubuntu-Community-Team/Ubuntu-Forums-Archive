---
title: "Help, school laptop wont boot, initramfs???"
date: 2009-03-04
forum: General Help
---

### Post by Kain000 on 2009-03-04
hey everyone, 

My laptop will no longer boot for me, worked fine lastnight I installed some updates and It was complaining that it was a partial update as some updates couldnt be installed, but it gave me the option for a partial so I selected it.

Shutdown  before I went to bed without issue, but today I tried to boot at school and grub would load the boot screen (ubuntu logo with the status bar) and the bar would just move back and fourth without starting to fill at all.    

after a few mins it will give me a black screen with 
```
(initramfs) _
```
where the underscore is blinking like a shell prompt.

I dont know what to do, I tried booting into recovery mode but it gets hung up while loading
```
begin: waiting for root file system... [   2.000230] Clocksource tsc unstable (delta = -92769551 ns)
```

3 mins or so later it will stop waiting and print:
```
gave up waiting for root device. Common problems:
-boot args (cat/proc/cmdline)
  -check rootdelay
  -check root
-missing modules (cat/proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/2ec1ec2b-5313-the rest of the HDD address- does not exist. Dropping to a shell!
(initramfs)_

```


NO IDEA what that means, I can speculate that it cant find or mount a root file system?  cant find the Hardrive?    It must as it can find grub and a kernel.

I tried to boot from a live usb that I have and rather than boot into the live gui, I have a ubuntu@ubuntu shell prompt.

perhaps if I can run a file system check but I dont know how to do that.  

by the way what is the command for a x-windows session?

---

### Post by khelben1979 on 2009-03-04
Okay.

```
startx
```
and
```
startx -- :2
```
if you want 2 graphical x-servers etc. etc.

You need to use [the fsck tool]("http://en.wikipedia.org/wiki/Fsck") to check the file system (see the wiki link).

You can also type:
```
man fsck
```
if you need some instructions on how to use the command.

---

### Post by sdennie on 2009-03-04
It sounds like either /boot/grub/menu.lst or /etc/fstab is corrupt.  Though not a fix, when at that initramfstab prompt, try:

```

mount /dev/sda1 /root
exit

```

Assuming your boot partition is /dev/sda1.  After that, check the two files I mentioned earlier to make sure they are ok.

---

### Post by geirha on 2009-03-04
It would help to see the partition table and your fstab. To get to that you can boot your ubuntu CD, and run in a terminal: ```
sudo fdisk -l
``` to see the partition table(s), and mount the root partition and post the content of etc/fstab on the root partition.

Is it possible you ran out of space on / when you installed those updates?

---

### Post by Kain000 on 2009-03-04
> **khelben1979 said:**
> Okay.

```
startx
```


thanks now I have my gui  back!


> **geirha said:**
> It would help to see the partition table and your fstab. To get to that you can boot your ubuntu CD, and run in a terminal: ```
sudo fdisk -l
``` to see the partition table(s), and mount the root partition and post the content of etc/fstab on the root partition.

Is it possible you ran out of space on / when you installed those updates?


Im sure there is enough space, acording to the live system 118 GB

I'm thinking that you are right as it is not finding/mounting the root partition.


here is the output from the fdisk -l command

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00080b83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 4076 MB, 4076863488 bytes
156 heads, 48 sectors/track, 1063 cylinders
Units = cylinders of 7488 * 512 = 3833856 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1064     3981288    c  W95 FAT32 (LBA)

```

Just ignore the /dev/sdb info, thats the usb drive I booted from.

---

### Post by Kain000 on 2009-03-04
here is the fstab file in the laptops drive. 

it seems fine to me but perhaps someone else has a better eye.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ec1ec2b-5313-40c9-9b87-a8e07c2eb314 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=20b9f26c-5022-4066-9ee1-a1deeca0c777 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
10.0.1.2:/home/sean/shared /home/sean/shared nfs rsize=1892,wsize=1892,timeo=14,intr
```

---

### Post by geirha on 2009-03-05
Your last line in fstab only has 4 fields. Add 0s for the dump and pass fields. That shouldn't cause the other entries to stop working though ...

Does the UUIDs in fstab match the UUIDs printed by blkid? ```
sudo blkid
``` 

Also, have you tried booting the previous kernel. Does that work?

---

### Post by Kain000 on 2009-03-05
> **geirha said:**
> Your last line in fstab only has 4 fields. Add 0s for the dump and pass fields. That shouldn't cause the other entries to stop working though ...

Does the UUIDs in fstab match the UUIDs printed by blkid? ```
sudo blkid
``` 

Also, have you tried booting the previous kernel. Does that work?

humm you are right, that last line is for my shared folder.  

I tried the other 2 kernel options it allows me and both give me the same error.

it's alright I got in with a live usb, and made a copy of my home folder, and tried to install over the previous system, however though I was able to read and wright to and from the inteinal drive, the installer's partitionar did not find the disk as being able to install to.

I then gave the whole system a good wipe with D-BAN and am planing to re-install this afternoon.  I will post back later today with the results.

Not sure what caused this mess in the first place but for the installer not to see my drive worries me.

---

### Post by geirha on 2009-03-06
It sounds like it might be trying to use the wrong driver for your SATA or IDE controller. You might be able to get around that by providing the proper options to the kernel, but I don't know which options that would be. Run ```
lspci
``` and search for the IDE/SATA controller model it shows on the internet. Chances are someone else has had similar problems and figured out how to work around it.

---

### Post by Kain000 on 2009-03-06
> **geirha said:**
> It sounds like it might be trying to use the wrong driver for your SATA or IDE controller. You might be able to get around that by providing the proper options to the kernel, but I don't know which options that would be. Run ```
lspci
``` and search for the IDE/SATA controller model it shows on the internet. Chances are someone else has had similar problems and figured out how to work around it.

thanks for the help.

I just went with a fresh install after the Dban wipe.  after the wipe the live USB found the drive and the install went fine.

now it's just time to re-configure everything.

lesson learned.....   image your drive before you need it. :(

---

### Post by entr3p on 2009-03-06
> **Kain000 said:**
> thanks for the help.

I just went with a fresh install after the Dban wipe.  after the wipe the live USB found the drive and the install went fine.

now it's just time to re-configure everything.

lesson learned.....   image your drive before you need it. :(

Or don't partially update ;).

---

