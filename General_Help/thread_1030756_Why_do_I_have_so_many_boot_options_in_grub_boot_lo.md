---
title: "Why do I have so many boot options in grub boot loader"
date: 2009-01-04
forum: General Help
---

### Post by lonewolf454 on 2009-01-04
After I ran out of available disk space on partition for linux/ext3 I now have two identical ubuntu login options and I also have two options for Windows Longhorn (which is Vista 32bit) which I had before system crashed.

The first option has usb support but no sound, and second ubuntu choice has sound but no usb. Before crash, I had one choice, and USB and sound worked.

Any suggestions?

---

### Post by sandyd on 2009-01-04
post the output of "sudo fdisk -l" please

boot ubuntu from a livecd if you can't use the version currently installed on your system.

---

### Post by lonewolf454 on 2009-01-04
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x645d1f0e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           18820       19457     5124735   82  Linux swap / Solaris
/dev/hda2   *         497        1276     6265350    7  HPFS/NTFS
/dev/hda3            1277       17258   128370786+   7  HPFS/NTFS
/dev/hda4               1         496     3984088+  83  Linux

Partition table entries are not in disk order

>>> Note:  I can boot without live cd, although I had to use it to resize ext3 partition, when system was crashed.  I am using linux/ubuntu now, without any sound, but usb modem working fine.  As I stated before, I always have one or the other but not both since I ran out of disk space, which I have since fixed by resizing partition.

---

### Post by sandyd on 2009-01-05
run fcsk (your ext3 partition might not have been resized correctly since it was full)

it it corrects errors and your ubuntu starts up fine, your lucky. 

it it doesnt.....

run this.....

```

sudo gedit /boot/grub/menu.lst
```
it should have something similar to what i have near the bottom of this post (other than the hard disk numbers) somewhere in it. if it doesn't, try commenting out all the ubuntu boot options out (except for your windows boot options). 

Meaning that you run this in terminal. 
```
cp /boot/grub/menu.lst /boot/grub/menu.lst-backup 
sudo gedit /boot/grub/menu.lst
```

then putting a "#" sign (without the quotes) in front of lines that resemble but not quite match the ones i have below. then just copy and past the stuff below into your menu.lst.   

NOTE: replace "root (hd0,4)" with the correct partition number. such as  "root (0,3)"

```

title Ubuntu 8.1, kernel 2.6.27-11-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=8870a466-03ba-4cdb-b0da-271cc36f1a12 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 8.1, kernel 2.6.27-11-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=8870a466-03ba-4cdb-b0da-271cc36f1a12 ro single
initrd /boot/initrd.img-2.6.27-11-generic

```

you also might want to try to reinstall grub, that might help
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5")

just start from that page of the tutorial.
the only difference is that you should enter your partition number in at where it says root (hd0,0)

if you can't figure out how to edit your menu.lst, post it right here

---

### Post by lonewolf454 on 2009-01-31
Carlee

I sort of took your advice and edited the grub menu.lst  I had a ver .19 and ver .22 showing, I am running version .19 so I commented out the two selections for ver .22 and now sound and usb is working.  It seems strange that had system screwed up, because before if I selected .19 I still only had sound/video support, now I have both.  

I am getting a startup screen though that shows everything that is booting DKMS is only thing it hangs on for a few seconds and fails. Then it goes to normal login screen.  Thanks for the help and suggestions.

---

