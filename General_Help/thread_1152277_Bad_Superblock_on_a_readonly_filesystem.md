---
title: "Bad Superblock on a readonly filesystem"
date: 2009-05-07
forum: General Help
---

### Post by dnbozss on 2009-05-07
(I'd like to apologize in advance for what seems like an overwhelming amount of information. I just want people to know what I've tried. I will try anything so if you have any thoughts at all, please share.)

I have an ASUS EEE 901 with WinXP installed, and I decided to install Crunchee (which I know is not Ubuntu, but very close) to an SD card and dual boot. everything worked fine until one day, I accidentally tried to boot up with the read only switch On on the SD card. I had to hard reset, since it hung at boot. Now whenever I try to boot, it hangs. Here's the message I get at every boot.

```
Boot from (hd0,0) ext3   2f543642-fdc7-4785-88e8-7140e9c283f0
Starting up ...
Loading, please wait ...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/5612049f-642b-4c48-bf9d-89c8d5abfe) = dev(8,37)
kinit: trying to resume from /dev/disk/by-uuid/5612049f-642b-4c48-bf9d-89c8d5abfe
kinit No resume image, doing normal boot...
[     13.268294] EXT2-fs: INFO: recovery required on readonly filesystem.
[     13.268373] EXT2-fs: write access unavailable, cannot proceed.
mount: mounting /dev/disk/by_uuid/2f543642-fdc7-4785-88e8-7140e9c283f0 on /root failed: invalid argument
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

(initramfs)_
```

To be clear it does make it past the GRUB, and even past the Crunchbang loading window.

So now, I'm thinking that the system is stuck in readonly somehow. After booting to a live Crunchee, I ran fdisk -l with the followng results:

```
Disk /dev/sdd:8118 MB, 8118075392 bytes
255 heads, 63 sectors/track, 986 cylinders
Units - cylinders of 16065 * 512 = 8445280 bytes
Disk identifier: 0x00cd56b

/dev/sdd1 *  1   938   7534453+  83  Linux
/dev/sdd2        986   38560     5   Extended
/dev/sdd5        986   38560+    5   Linux swap / Solaris

```

When I try to run fsck /dev/sdd1, I get

```
fsck.ext3: Read-only file system while trying to open /dev/sdd1
Disk write-protected; use the -n option to do a read-only check of the device
```

and when I do, I get a huge long code with the last lines being

```
Directory inode 235713, block 0, offset 0: directory corrupted
Salve? no

ef2sck: aborted
```

I tried running mk2fs -n /dev/sdd1, and I got

```
Read-only file system while setting up superblock
```

Lastly, I try a simple mount, and get this

```
~$sudo mount -t ext3 /dev/sdd1 /mnt
mount: block device /dev/sdd1 is write-protected, mounting read-only
mount: wrong fstype, bad option, bad superblock on /dev/sdd1, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail or so
```

So I tried dmesg | tail and got a ton of stuff, but basically all along the lines of
```
VFS: Can't find ext3 filesystem on dev sdd.
EXT3-fs: INFO: recovery required on readonly filesystem.
```


I've tried everything I can think of, even if I'm a linux noob. I tried backing up the partition with PartImage, but it failed. I've read threads like

[http://ubuntuforums.org/showthread.php?t=656769](http://ubuntuforums.org/showthread.php?t=656769)
[http://ubuntuforums.org/showthread.php?t=243525](http://ubuntuforums.org/showthread.php?t=243525)

and I've posted this problem in both the EEEuser and Crunchbang forums, and both gave me no responses.


It's like no matter what I do, I can't do it because it's read only. So I need to know two things:
(1) Can I fix it? If so, how? (Like what does "recovery required" mean?)
(2) If not, is the disk toast? (IE, can I install and start over?)

I'm really hoping I get some responses from this, since it's been unsuccessful in two other forums. If it motivates you any more, I was considering switching to Linux as my primary OS until this happened, and if someone can fix it for me, I might still.

Thanks in advance.
-Pie

---

### Post by dnbozss on 2009-05-07
Well, it looks like I'm getting my files off of it at least. I used [DiskInternals Linux Reader]("http://www.diskinternals.com/linux-reader/") for Windows to backup the partition to a .dsk file, then I used [R-Linux]("http://www.data-recovery-software.net/Linux_Recovery.shtml") to open that .dsk file, and I was able to recover many of my files. It's still going, and may end out recovering through the night, but at least it's working. Hopefully it won't get hung up on a broken file.

I'm kind of disappointed though, in that this is the third forum that I've posted my problem in, and it's the third forum that hasn't really helped at all. Given that there are at least 600 members on at any time, I thought that at least one could take the time to suggest something. But it's fallen 8 pages without one reply, and I hate to bump my own thread, but I do want to post how I kind of solved the problem in case someone else encounters it after me.

But still, even after I get the files off, I need to know if I can still use the card. So here's a very simple question that I hope someone can answer:

If I were to repartition my card (I haven't tried yet so I don't even know if it will let me), would that help or hurt what's wrong with the write protection?

---

### Post by lensman3 on 2009-05-07
You have dropped into a ramdisk recovery level.  See the prompt in the first screen "initramfs".  I think the boot kernels temp file system is corrupt or missing.  These are the files in /boot that start with initrd-build_number.   

You will have to use the program "mkinitrd" from a recovery disk.  Use the chroot program to remount the hard drive root filesystem and real /boot partition.    Don't forget the -f flag because it will take an existing initrd-xxxx and rewrite the file.  

I converted my root file system from ext3 to ext4.  When I did a reboot and after /etc/fstab, my initrd ram disk didn't have the ext4 disk driver.  Ext4 wasn't compiled into the kernel and it wasn't in the boot ramdisk (initrd).  I had to use a rescue disk, chroot, run mkinitrd to add the ext4 module.  It took me 1/2 and hour to figure out the -f flag was need to rewrite the file.  The initrd file is actually a cpio, gzip'd file system that has everything the booting kernel needs when it goes to run-level 1.  The reboot after that worked.

Hope this helps (a little).

---

### Post by dnbozss on 2009-05-08
lensman, I don't think it's just the the kernel, because I can't even mount it in a live environment. But I'll give it a shot.

Are you sure that this will work? It's late at night here, and I'm tired so I can't try until tomorrow.

EDIT: Dumb question, what's a recovery disk? Just a live Crunchee? Is mkinitrd included?

---

### Post by dnbozss on 2009-05-10
I really hate to be a bumper, but it's been two days, and it's dropped 43 pages with only one response.

I still need to know, how do I switch my filesystem off write protection? I got all my files off of it, so I don't care if I have to whipe it clean. I was thinking maybe deleting the partition and making a new one might help, but I really don't know exactly what a SuperBlock is, and I'm kind of afraid that doing anything at this point might end out hurting rather than helping. (That's how it seems with Linux: Nothing does nothing. Everything either hurts or helps.)

This is all very disheartening for a Linux newbie.

---

