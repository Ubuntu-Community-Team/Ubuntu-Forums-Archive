---
title: "Can't boot to WindowsXP Pro"
date: 2006-01-14
forum: General Help
---

### Post by stone on 2006-01-14
Hi everyone,

I recently installed Ubuntu and I'm loving it so far, but I have one major problem. I set my computer up to dual boot and now I can't get into WindowsXP! When I start my computer and get to the boot menu if I choose Windows I get a black screen, then my computer restarts and I am back at the boot menu.

Maybe I messed something up when I partitioned my hard drive? The strange thing is that I can mount my Windows partition and access it from Ubuntu, so it can't be *that* messed up. Also, when I created my partitions I made sure to create my Ubuntu partition at the end of the disk because I've read here that Windows likes to be on the first partition.

So does anybody have any ideas? Thanks in advance!

---

### Post by fourchannel on 2006-01-14
can you paste the contents of ```
/boot/grub/menu.lst
``` cause it sounds like your chainloader is misconfigured.
 
EDIT:
 
or ```
/etc/lilo.conf
``` if you are using lilo. ubuntu defaults to grub though...
 
and ```
/etc/fstab
``` also, so we can see how your harddrive is setup.

---

### Post by stone on 2006-01-15
Thanks for the response! You are right, I am using GRUB. Here's my /boot/grub/menu.lst file (I've removed comments for brevity... everything above this was commented out):

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1






----------------------------------------
and here's my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



hmm... the funny thing is that /dev/hda1 doesn't show up in my fstab file... but that's where my Windows lives. I don't know if that is significant though.

Anyway, here's my disk setup in English:
I had two hard drives. The first had Windows XP Pro as NTFS, the second had a bunch of files as FAT32. I didn't touch the second drive, but I partitioned the first so that it would have 4 partitions:
1) Windows XP on NTFS
2) Ubuntu on ext3
3) Swap
4) Fat32 (so I could share files between Windows and Ubuntu)

---

### Post by kosmic on 2006-01-15
Please do in a terminal :
 
sudo fdisk -l (it is a L)
 
and post the results

---

### Post by bonzodog on 2006-01-15
try adding the word 'boot' below  'chainloader +1'. (you will see the ubuntu entries above have it).

---

### Post by cotcot on 2006-01-15
I have the same dual boot with this at the end in menu.lst

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

So no "make active" and no "boot". Maybe try to set your hda1 (the XP partition) active after ubuntu install.  (ubuntu sets the ubuntu partition active during install). It worked in my situation. (can be done with fdisk)

---

### Post by stone on 2006-01-15
Here's what I get when I run fdisk -l

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7295    58597056    7  HPFS/NTFS
/dev/hda2           14406       19457    40580190    5  Extended
/dev/hda3            7296       14405    57111075   83  Linux
/dev/hda5           14595       19457    39062047+   b  W95 FAT32
/dev/hda6           14406       14593     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)

```

> 
Maybe try to set your hda1 (the XP partition) active after ubuntu install. (ubuntu sets the ubuntu partition active during install). It worked in my situation. (can be done with fdisk)
How do I go about doing that? Could you point me to a good fdisk tutorial/explanation?

---

### Post by stone on 2006-01-15
Just an update: I tried adding "boot" under "chainloader +1" and restarting, but it didn't make a difference. Please keep those ideas coming! :smile: Thanks!

---

### Post by TomPreuss on 2006-01-16
Stone, I just wanted to let you know that I seem to be having a very similar problem.

I posted about it in [this thread](http://www.ubuntuforums.org/showthread.php?t=117791), so you might want to keep an eye on that as well.

So far I have not had any success, but if I make any progress, I'll be sure to let you know.

---

### Post by inigmatus on 2006-01-16
Was this a partition resizing job?

If not, then I wonder if getting rid of Grub and then reloading it would work. 

[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630) details getting rid of Grub easily. Reinstalling it is another matter - but I think u just skip the options to install anything on the Ubuntu Install CD and head straight for Grub and reload it to your MBR.

---

### Post by stone on 2006-01-23
So I've done some research and here's what it seems like. It looks like the chainloader is working correctly because I actually get to NTLDR (I get a screen with options to boot Windows in regular mode, safe mode and all that stuff). If I pick Safe Mode then a bunch of .dll's all flash by prefixed with "multi(0)disk(0)rdisk(0)partition(1)\WINDOWS" which is what it says in my Window's boot.ini file. After that I get a black screen and my computer restarts.

To inigmatus: yes, I did partition my drive as I installed Ubuntu. I'm not sure if reinstalling GRUB will be worth it though, since it seems to be doing its job.

So is it possible I messed something up when partitioning my drive? Whatever I did, Windows isn't happy with it :p  Anyone have any more ideas, or even another forum or website where I can get some info? Thanks.

---

