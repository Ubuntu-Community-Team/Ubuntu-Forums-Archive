---
title: "Ext4 File System Unsupported in Jaunty Error"
date: 2009-06-01
forum: General Help
---

### Post by AmbientOcclusion on 2009-06-01
I formatted a USB thumbdrive in gparted to ext4.

I am using Ubuntu 9.04 upgraded from 8.10 upgraded from 8.04.

When I tried to mount/plug in the drive I get a message stating that ext4 filesystems are not supported on my system.

[img]http://img208.imageshack.us/img208/2594/screenshot2wxx.png[/img]

Here is the output of 

sudo fdisk -l

> Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13901390

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30427   244404846   83  Linux
/dev/sda2   *       30428       34999    36724590    7  HPFS/NTFS
/dev/sda3           35000       36481    11904165    5  Extended
/dev/sda5           35000       36481    11904133+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x225a2221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 507 MB, 507322880 bytes
255 heads, 63 sectors/track, 61 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x954e753c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          61      489951   83  Linux


If I double click on the icon in my computer browser it will sometimes pop up this window over the "not supported error message:"

[img]http://img523.imageshack.us/img523/7787/screenshot3d.png[/img]

After a delay this window pops up:

[img]http://img142.imageshack.us/img142/5006/screenshot1r.png[/img]
> **Unable to Mount Location**

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Not really sure what is going on...

Thanks ahead of time for any help.

I am running 9.04. 
> $ cat /etc/issue Returns

> Ubuntu 9.04 \n \l

---

### Post by AmbientOcclusion on 2009-06-01
Here is some more info.

> cat /etc/fstab

*Returns:*

> proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=a275a0a0-f1e3-4ee5-bfe5-29b96baf9437 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=02f1d613-709a-428a-8846-6d9d3bf1c902 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/SATA_Internal500 auto defaults 0 1


I have tried sudo apt-get dist-upgrade for good measure thinking it was something to do with Dbus, but I am lost.

---

### Post by oldos2er on 2009-06-01
Can you post the output of **uname -r** run in a terminal?

---

### Post by AmbientOcclusion on 2009-06-01
Hi.

The output is:

**2.6.24-22-generic**

---

### Post by oldos2er on 2009-06-01
That's the problem; only kernel version 2.6.28.* support ext4.

---

### Post by binbash on 2009-06-01
Yes, that kernel is not supported.That is the problem

---

### Post by AmbientOcclusion on 2009-06-01
Oh okay. What can I do to resolve this problem...

I thought I would have the latest kernel tho' when I did my update.

---

### Post by binbash on 2009-06-01
install one from here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by AmbientOcclusion on 2009-06-01
> **binbash said:**
> install one from here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)Thanks for that link.

Which kernel would you recommend for 64 bit?

Any possible guide to help me along would be cool as well, I have never updated the kernel before, usually I just do updates thru the manager.

Thanks for the help.

---

### Post by oldos2er on 2009-06-01
Can you post the output of **ls /boot/vml*** ?

---

### Post by AmbientOcclusion on 2009-06-01
Here is the output:

/boot/vmlinuz-2.6.24-19-generic  /boot/vmlinuz-2.6.24-24-generic
/boot/vmlinuz-2.6.24-21-generic  /boot/vmlinuz-2.6.28-11-generic
/boot/vmlinuz-2.6.24-22-generic  /boot/vmlinuz-2.6.29-02062904-generic
/boot/vmlinuz-2.6.24-23-generic


.

---

### Post by AmbientOcclusion on 2009-06-01
/boot/grub/menu.lst displays:

> title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a275a0a0-f1e3-4ee5-bfe5-29b96baf9437 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a275a0a0-f1e3-4ee5-bfe5-29b96baf9437 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title    MS Windows XP
root     (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by AmbientOcclusion on 2009-06-01
During the upgrade is it possible that I held onto the old menu.lst or something?

---

### Post by oldos2er on 2009-06-01
> **AmbientOcclusion said:**
> During the upgrade is it possible that I held onto the old menu.lst or something?

 Yes, that's what it looks like. Try running ```
sudo update-grub
``` to see if you can generate a fresh menu.lst.

---

### Post by AmbientOcclusion on 2009-06-01
I did this and returned these results:

> Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29-02062904-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


However, when i check the menu.lst it still displays:
> title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a275a0a0-f1e3-4ee5-bfe5-29b96baf9437 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a275a0a0-f1e3-4ee5-bfe5-29b96baf9437 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title    MS Windows XP
root     (hd0,1)
savedefault
makeactive
chainloader    +1

What would be the best way to change this?

---

### Post by oldos2er on 2009-06-01
I wonder if you're booting from an older grub. Can you post the output of
```
grub --version
```
?

---

### Post by AmbientOcclusion on 2009-06-01
Weird if it is.

Here is the output:
> grub (GNU GRUB 0.97)

---

### Post by oldos2er on 2009-06-01
Ok, your Grub version looks good. Open your menu.lst file
```
gksu gedit /boot/grub/menu.lst
```and add this at the bottom of the file
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a275a0a0-f1e3-4ee5-bfe5-29b96baf9437 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
``` Save it, exit the file, reboot into the new kernel, and hopefully you'll have ext4 support.

---

### Post by AmbientOcclusion on 2009-06-01
Thanks for your help! 

Everything works and I can boot into the new kernel with ext4 support...

---

