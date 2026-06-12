---
title: "Erased /boot partition by accident"
date: 2009-01-14
forum: General Help
---

### Post by Munkoil on 2009-01-14
To make a long story short, I wanted to resize my /boot partition. Something went very wrong, I lost the data and I couldn't get it back. I hoped for some sort of rescue/repair on the install cd and rebooted. Now I understand I maybe could have fixed it right away, but I didn't.

My situation now is that I can't boot my computer. Is there any way to restore /boot partition and grub without reinstalling my system?

I've tried to mount my /boot partition to /boot using the live-cd and reinstalled a kernel. Now grub gets error 15. This I think is because grub is not installed/configured on the partition yet. Can I configure grub in the same way and do i need to install something else than the linux-image package to /boot? Is this the way to do it or is there a better approach?

---

### Post by BazookaAce on 2009-01-14
Welcome to the club! I managed to do the same thing. My solution? Re-installed the whole thing. But do you have something important on your computer?

---

### Post by caljohnsmith on 2009-01-14
Fortunately in most cases you can rebuild your boot partition even after deleting it with a little bit of work; how about posting the output of:
```
sudo fdisk -lu
```
And identify which is your boot partition and your main Ubuntu partition, and we can work from there.

---

### Post by Munkoil on 2009-01-15
> **caljohnsmith said:**
> Fortunately in most cases you can rebuild your boot partition even after deleting it with a little bit of work; how about posting the output of:
```
sudo fdisk -lu
```
And identify which is your boot partition and your main Ubuntu partition, and we can work from there.

Sounds good!

The output is
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00006e98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c79a218

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000182f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   390716864   195358401   83  Linux

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c79a219

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   390716864   195358401   83  Linux

Disk /dev/sde: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e7fd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63      417689      208813+  83  Linux
/dev/sde2          417690     4048379     1815345   82  Linux swap / Solaris
/dev/sde3         4048380    72292499    34122060   83  Linux

Disk /dev/sdf: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001a55e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63    72292499    36146218+  83  Linux

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3e9c9b40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   976768064   488384001   fd  Linux raid autodetect

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34f13278

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63   976768064   488384001   83  Linux
```

The harddrives are mounted as follows

```

<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sde1     /boot           ext2    relatime        0       2
/dev/sde2     none            swap    sw              0       0
/dev/sde3     /               ext3    relatime        0       2

```

Grub is installed to MBR on /dev/sda.

---

### Post by caljohnsmith on 2009-01-15
OK, how about trying the following:
```
sudo mount /dev/sde3 /mnt
sudo mount /dev/sde1 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
ls /lib/modules
```
The directories in the /lib/modules should tell you which kernels you had installed before deleting the boot partition, so then do:
```
apt-get purge linux-image-2.6.24-16-generic
apt-get install linux-image-2.6.24-16-generic
```
But replace the kernel above with whichever are the kernels you want to reinstall. If you can install the kernels successfully, continue with:
```
grub-install /dev/sda  --recheck
update-grub
exit
```
You said you wanted Grub installed to the MBR of sda, but if you do that using the standard grub-install method as shown above (the same method the Ubuntu installer uses), then on start up Grub will be looking on the 5th boot drive for its boot files; so the only way you can make that work is if you have your sde drive 5th in the BIOS boot order. I think a much better way would be to install Grub to the same drive Ubuntu is on (sde), and then simply change your BIOS to boot the sde drive. It's up to you though. Anyway, let me know how it goes or if you run into problems.

---

### Post by Munkoil on 2009-01-15
After i reinstalled the kernel i got this error
```
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.24-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Looks like the following line solved that problem
```
 sudo dpkg --configure -a 
```

After that when I tried to run
```
root@ubuntu:/boot/grub# sudo grub-install /dev/sda --recheck
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

I'm currently looking for a solution for that problem.

---

### Post by Munkoil on 2009-01-15
I've solved that problem now by unmounting and mounting /boot to another directory and then using grub-install with --root-directory=DIR option. When i mounted the volume back to /boot it even work with grub-install without --root-directory.

The rest went fine but when I rebooted I got error 22 in grub. Looks like I have to do some more research.

---

### Post by caljohnsmith on 2009-01-15
> **Munkoil said:**
> I've solved that problem now by unmounting and mounting /boot to another directory and then using grub-install with --root-directory=DIR option. When i mounted the volume back to /boot it even work with grub-install without --root-directory.

The rest went fine but when I rebooted I got error 22 in grub. Looks like I have to do some more research.
I warned you that would happen; unless you make your sde drive exactly 5th in the BIOS boot order, you will get Grub errors with the way Grub is currently installed to your sda drive. It would be much better I think to simply install Grub to the Ubuntu drive and then boot the Ubuntu drive, but it's your choice.

---

### Post by Munkoil on 2009-01-15
Yes, I finally figured it out. In some way the order of the disks was different in grub then when I booted the system. I finally fixed it. The good thing about when stuff like this happens is that you learn alot how stuff really works on your computer. Thank you for all your help! I will be more careful in the future.

---

