---
title: "cannot boot ubuntu. gparted cannot read ext3 partition."
date: 2009-01-28
forum: General Help
---

### Post by Tuxoid on 2009-01-28
Last night, my brother was using my ubuntu laptop. He was using firefox to listen to a podcast, and left it it to play the PS3. He needed to look up a guide on youtube, but while on youtube, the entire OS was locking up. Eventually, firefox crashed, and continually did so. So he restarted the computer, but it did not restart correctly, and hung, so he needed to hold down the power button. A few minutes later, he turned the computer back on. This time, The computer said 'Operating System not found', on boot.

The next morning, I attempted to salvage the system. Firstly, I loaded the BIOS set up, and noticed there was no Hard Drive listed. I attempted to boot a LiveCD, and it did not run. I tried the same CD in my dad's desktop, and it booted fine.

So I turned off my laptop, opened the hard drive hatch, and saw a loose connection. I fixed it, turned on my computer, and it would now boot the LiveCD, but not my installed system. When trying to boot from the HD, it would just post 'GRUB' on the top of the screen, and wouldn't go past that. I immediately loaded the LiveCD, and ran Gparted. it saw my Hard Disk, but it could not read the ext3 partition where all my data is, and could not tell what filesystem it was using. I desperately attempted to do things, like turn swap off, and delete swap and make a new swap. I ran badblocks, and it found no bad blocks on my disk. I used the quick search, and deeper search modes, but to no avail. It found the correct partitions, but I was unable to do anything to fix my problem.

I really don't think my filesystem is dead, I think it can be fixed, but I feel like I'm stabbing in the dark.

does anyone know how I could recover my system?

---

### Post by hansdown on 2009-01-28
Hi Tuxoid.

A fresh install may be your easist solution.
Hard shut downs can mess things up.
For future reference,```
 hit ctrl> alt> backspace
```.
If that doesn't work,```
 hold alt> printscreen and press reisub to restart
```.
You can find that command on the ubuntu cheat sheet from fosswire.

[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

---

### Post by Tuxoid on 2009-01-28
Both my brother and I know of the 'ctrl alt backspace' shortcut, but in this situation it wasn't working.

From what I know about the problem, I believe the filesystem can be recovered, and I am in the process of finding out how. The hard drive is not physically damage.

I checked the disk using 'sudo fdisk -l'. Here's the output:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000333fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14350     1052257+   5  Extended
/dev/sda5           14220       14350     1052226   82  Linux swap / Solaris
```

according to testdisk, the superblock is still there, and has located it.
testdisk cannot read the contents of the partition, however.

I'd rather try my options before resulting in a re-install, as I cannot back-up anything, as there is no way to read the Linux partition.

---

### Post by bumanie on 2009-01-28
See you've already tried testdisk, that's what I was going to suggest. To me (and I could be wrong) it sounds a bit like the partition table has been corrupted. Testdisk should be able to recover that - from memory, I think an image of the partition table is stored elsewhere on the hard drive and testdisk will copy that and then re-write it. Failing that, you should be able to recover most of your files via photorec. It is recommended for these types of issues to clone the original hard drive to an external hard drive and use the cloned image to attempt recovery, that way the original is still intact and can be cloned again if the first attempts at recovery are not successful. There are other open source recovery programs which you should be able to find on google - sorry can't remember their names right now. Ahh...sleuthkit, with its GUI frontend, autopsy is one, that just came to mind and scalpel and foremost.

---

### Post by caljohnsmith on 2009-01-28
Have you tried doing an "fsck" yet on the partition to check and try to fix its file system? If not, please post the output of:
```
sudo fsck -yCM /dev/sda1
```

---

### Post by Tuxoid on 2009-01-28
I don't know if this is relevant, but for some reason, testdisk is seeing an HFS partition, along with the Linux partition. However, I don't have an HFS partition, as I don't run MacOS.

---

### Post by Tuxoid on 2009-01-28
output:

```
Free inodes count wrong for group #685 (16384, counted=16348).
Fix? yes

Directories count wrong for group #685 (0, counted=2).
Fix? yes

Free inodes count wrong for group #686 (16384, counted=16380).
Fix? yes

Directories count wrong for group #686 (0, counted=2).
Fix? yes

Free inodes count wrong for group #687 (16384, counted=15838).
Fix? yes

Directories count wrong for group #687 (0, counted=34).
Fix? yes

Free inodes count wrong for group #688 (16384, counted=15503).
Fix? yes

Directories count wrong for group #688 (0, counted=64).
Fix? yes

Free inodes count wrong for group #689 (16384, counted=12770).
Fix? yes

Directories count wrong for group #689 (0, counted=61).
Fix? yes

Free inodes count wrong for group #690 (16384, counted=15601).
Fix? yes

Directories count wrong for group #690 (0, counted=59).
Fix? yes

Free inodes count wrong for group #691 (16384, counted=15359).
Fix? yes

Directories count wrong for group #691 (0, counted=151).
Fix? yes

Free inodes count wrong for group #692 (16384, counted=15610).
Fix? yes

Directories count wrong for group #692 (0, counted=78).
Fix? yes

Free inodes count wrong for group #693 (16384, counted=16281).
Fix? yes

Directories count wrong for group #693 (0, counted=21).
Fix? yes

Free inodes count wrong for group #694 (16384, counted=16372).
Fix? yes

Directories count wrong for group #694 (0, counted=3).
Fix? yes

Free inodes count wrong for group #696 (16384, counted=16382).
Fix? yes

Free inodes count wrong for group #698 (16384, counted=16375).
Fix? yes

Free inodes count wrong for group #700 (16384, counted=16337).
Fix? yes

Free inodes count wrong for group #701 (16384, counted=15870).
Fix? yes

Directories count wrong for group #701 (0, counted=9).
Fix? yes

Free inodes count wrong for group #702 (16384, counted=15997).
Fix? yes

Directories count wrong for group #702 (0, counted=34).
Fix? yes

Free inodes count wrong for group #703 (16384, counted=16267).
Fix? yes

Directories count wrong for group #703 (0, counted=32).
Fix? yes

Free inodes count wrong for group #704 (16384, counted=16378).
Fix? yes

Free inodes count wrong for group #707 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #708 (16384, counted=16186).
Fix? yes

Free inodes count wrong for group #709 (16384, counted=16358).
Fix? yes

Free inodes count wrong for group #710 (16384, counted=16276).
Fix? yes

Directories count wrong for group #710 (0, counted=28).
Fix? yes

Free inodes count wrong for group #711 (16384, counted=16259).
Fix? yes

Directories count wrong for group #711 (0, counted=12).
Fix? yes

Free inodes count wrong for group #712 (16384, counted=15337).
Fix? yes

Directories count wrong for group #712 (0, counted=51).
Fix? yes

Free inodes count wrong for group #713 (16384, counted=16375).
Fix? yes

Directories count wrong for group #713 (0, counted=7).
Fix? yes

Free inodes count wrong for group #714 (16384, counted=16382).
Fix? yes

Free inodes count wrong for group #716 (16384, counted=16382).
Fix? yes

Free inodes count wrong for group #717 (16384, counted=16336).
Fix? yes

Directories count wrong for group #717 (0, counted=2).
Fix? yes

Free inodes count wrong for group #718 (16384, counted=13020).
Fix? yes

Directories count wrong for group #718 (0, counted=39).
Fix? yes

Free inodes count wrong for group #719 (16384, counted=16379).
Fix? yes

Free inodes count wrong for group #722 (16384, counted=16043).
Fix? yes

Directories count wrong for group #722 (0, counted=13).
Fix? yes

Free inodes count wrong for group #723 (16384, counted=16352).
Fix? yes

Free inodes count wrong for group #724 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #726 (16384, counted=16369).
Fix? yes

Directories count wrong for group #726 (0, counted=1).
Fix? yes

Free inodes count wrong for group #729 (16384, counted=16317).
Fix? yes

Directories count wrong for group #729 (0, counted=16).
Fix? yes

Free inodes count wrong for group #734 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #738 (16384, counted=16377).
Fix? yes

Free inodes count wrong for group #739 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #743 (16384, counted=16382).
Fix? yes

Free inodes count wrong for group #745 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #746 (16384, counted=16378).
Fix? yes

Free inodes count wrong for group #747 (16384, counted=16346).
Fix? yes

Free inodes count wrong for group #748 (16384, counted=16369).
Fix? yes

Free inodes count wrong for group #749 (16384, counted=16375).
Fix? yes

Free inodes count wrong for group #750 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #751 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #753 (16384, counted=16362).
Fix? yes

Free inodes count wrong for group #754 (16384, counted=16221).
Fix? yes

Free inodes count wrong for group #756 (16384, counted=16363).
Fix? yes

Directories count wrong for group #756 (0, counted=4).
Fix? yes

Free inodes count wrong for group #758 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #760 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #761 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #762 (16384, counted=16262).
Fix? yes

Free inodes count wrong for group #763 (16384, counted=16373).
Fix? yes

Directories count wrong for group #763 (0, counted=1).
Fix? yes

Free inodes count wrong for group #764 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #766 (16384, counted=16374).
Fix? yes

Free inodes count wrong for group #769 (16384, counted=16383).
Fix? yes

Directories count wrong for group #769 (0, counted=1).
Fix? yes

Free inodes count wrong for group #770 (16384, counted=16378).
Fix? yes

Free inodes count wrong for group #772 (16384, counted=16370).
Fix? yes

Directories count wrong for group #772 (0, counted=5).
Fix? yes

Free inodes count wrong for group #776 (16384, counted=16379).
Fix? yes

Free inodes count wrong for group #779 (16384, counted=16362).
Fix? yes

Directories count wrong for group #779 (0, counted=4).
Fix? yes

Free inodes count wrong for group #781 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #782 (16384, counted=16295).
Fix? yes

Directories count wrong for group #782 (0, counted=33).
Fix? yes

Free inodes count wrong for group #783 (16384, counted=16339).
Fix? yes

Directories count wrong for group #783 (0, counted=1).
Fix? yes

Free inodes count wrong for group #784 (16384, counted=16350).
Fix? yes

Directories count wrong for group #784 (0, counted=18).
Fix? yes

Free inodes count wrong for group #785 (16384, counted=13495).
Fix? yes

Directories count wrong for group #785 (0, counted=321).
Fix? yes

Free inodes count wrong for group #786 (16384, counted=16359).
Fix? yes

Directories count wrong for group #786 (0, counted=1).
Fix? yes

Free inodes count wrong for group #787 (16384, counted=16313).
Fix? yes

Directories count wrong for group #787 (0, counted=12).
Fix? yes

Free inodes count wrong for group #788 (16384, counted=16379).
Fix? yes

Free inodes count wrong for group #790 (16384, counted=16364).
Fix? yes

Directories count wrong for group #790 (0, counted=1).
Fix? yes

Free inodes count wrong for group #793 (16384, counted=16380).
Fix? yes

Free inodes count wrong for group #794 (16384, counted=16363).
Fix? yes

Directories count wrong for group #794 (0, counted=9).
Fix? yes

Free inodes count wrong for group #795 (16384, counted=15675).
Fix? yes

Free inodes count wrong for group #796 (16384, counted=16380).
Fix? yes

Free inodes count wrong for group #797 (16384, counted=16379).
Fix? yes

Free inodes count wrong for group #798 (16384, counted=16264).
Fix? yes

Free inodes count wrong for group #800 (16384, counted=16379).
Fix? yes

Free inodes count wrong for group #801 (16384, counted=16378).
Fix? yes

Free inodes count wrong for group #802 (16384, counted=16382).
Fix? yes

Free inodes count wrong for group #803 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #804 (16384, counted=16381).
Fix? yes

Free inodes count wrong for group #811 (16384, counted=16335).
Fix? yes

Directories count wrong for group #811 (0, counted=11).
Fix? yes

Free inodes count wrong for group #814 (16384, counted=16105).
Fix? yes

Free inodes count wrong for group #815 (16384, counted=16377).
Fix? yes

Free inodes count wrong for group #816 (16384, counted=16381).
Fix? yes

Free inodes count wrong for group #817 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #824 (16384, counted=16364).
Fix? yes

Directories count wrong for group #824 (0, counted=4).
Fix? yes

Free inodes count wrong for group #826 (16384, counted=16381).
Fix? yes

Free inodes count wrong for group #828 (16384, counted=16188).
Fix? yes

Directories count wrong for group #828 (0, counted=19).
Fix? yes

Free inodes count wrong for group #829 (16384, counted=16368).
Fix? yes

Free inodes count wrong for group #830 (16384, counted=16359).
Fix? yes

Directories count wrong for group #830 (0, counted=4).
Fix? yes

Free inodes count wrong for group #831 (16384, counted=16307).
Fix? yes

Directories count wrong for group #831 (0, counted=6).
Fix? yes

Free inodes count wrong for group #832 (16384, counted=16358).
Fix? yes

Directories count wrong for group #832 (0, counted=6).
Fix? yes

Free inodes count wrong for group #833 (16384, counted=16352).
Fix? yes

Free inodes count wrong for group #834 (16384, counted=16355).
Fix? yes

Free inodes count wrong for group #835 (16384, counted=16359).
Fix? yes

Free inodes count wrong for group #836 (16384, counted=16360).
Fix? yes

Free inodes count wrong for group #837 (16384, counted=16360).
Fix? yes

Free inodes count wrong for group #838 (16384, counted=16360).
Fix? yes

Free inodes count wrong for group #839 (16384, counted=16379).
Fix? yes

Directories count wrong for group #839 (0, counted=1).
Fix? yes

Free inodes count wrong for group #840 (16384, counted=16369).
Fix? yes

Free inodes count wrong for group #841 (16384, counted=16380).
Fix? yes

Free inodes count wrong for group #842 (16384, counted=16352).
Fix? yes

Free inodes count wrong for group #843 (16384, counted=16344).
Fix? yes

Free inodes count wrong for group #844 (16384, counted=16355).
Fix? yes

Free inodes count wrong for group #845 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #846 (16384, counted=16382).
Fix? yes

Free inodes count wrong for group #847 (16384, counted=16340).
Fix? yes

Free inodes count wrong for group #849 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #851 (16384, counted=16323).
Fix? yes

Free inodes count wrong for group #852 (16384, counted=16378).
Fix? yes

Free inodes count wrong for group #853 (16384, counted=16380).
Fix? yes

Free inodes count wrong for group #856 (16384, counted=16377).
Fix? yes

Free inodes count wrong for group #857 (16384, counted=16380).
Fix? yes

Free inodes count wrong for group #858 (16384, counted=16305).
Fix? yes

Directories count wrong for group #858 (0, counted=1).
Fix? yes

Free inodes count wrong for group #860 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #862 (16384, counted=16361).
Fix? yes

Directories count wrong for group #862 (0, counted=3).
Fix? yes

Free inodes count wrong for group #863 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #864 (16384, counted=16383).
Fix? yes

Free inodes count wrong for group #866 (16384, counted=16337).
Fix? yes

Free inodes count wrong for group #867 (16384, counted=16378).
Fix? yes

Free inodes count wrong for group #869 (16384, counted=16379).
Fix? yes

Free inodes count wrong for group #870 (16384, counted=16072).
Fix? yes

Directories count wrong for group #870 (0, counted=26).
Fix? yes

Free inodes count wrong for group #871 (16384, counted=16365).
Fix? yes

Free inodes count wrong (14286837, counted=13630853).
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 655995/14286848 files (2.0% non-contiguous), 20374025/28553521 blocks
```

---

### Post by caljohnsmith on 2009-01-28
How about running the fsck one more time to make sure it fixed everything as well as it could, and then try:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
And please post the output.

---

### Post by Tuxoid on 2009-01-28
```
total 132
drwxr-xr-x   2 root root   4096 2008-12-19 13:44 bin
drwxr-xr-x   3 root root   4096 2008-12-17 13:20 boot
lrwxrwxrwx   1 root root     11 2008-04-04 15:24 cdrom -> media/cdrom
drwxr-xr-x   4 root root  12288 2008-10-31 13:04 dev
drwxr-xr-x 163 root root  12288 2009-01-28 06:01 etc
drwxrwxr-x   5 root root   4096 2008-05-07 13:26 home
drwxr-xr-x   2 root root   4096 2007-10-15 23:17 initrd
lrwxrwxrwx   1 root root     32 2008-11-28 03:08 initrd.img -> boot/initrd.img-2.6.27-9-generic
lrwxrwxrwx   1 root root     32 2008-10-31 12:59 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  17 root root  12288 2009-01-07 08:03 lib
drwx------   2 root root  16384 2008-04-04 15:23 lost+found
drwxr-xr-x   4 root root   4096 2009-01-28 06:00 media
drwxr-xr-x   2 root root   4096 2007-10-08 10:47 mnt
-rw-r--r--   1 1000  1000  2184 2008-03-01 03:25 modprobe.d
drwxr-xr-x   2 root root   4096 2007-10-15 23:17 opt
drwxr-xr-x   2 root root   4096 2007-10-08 10:47 proc
drwxr-xr-x  33 root root   4096 2009-01-20 06:24 root
drwxr-xr-x   2 root root   4096 2009-01-07 08:03 sbin
drwxrwxrwx   9 1000 users  4096 2008-08-15 18:29 Shared
drwxr-xr-x   2 root root   4096 2007-10-15 23:17 srv
drwxr-xr-x   2 root root   4096 2007-10-04 11:17 sys
drwxrwxrwt  13 root root  12288 2009-01-28 06:04 tmp
drwxr-xr-x  14 root root   4096 2008-06-14 03:36 usr
drwxr-xr-x  16 root root   4096 2008-05-10 16:34 var
lrwxrwxrwx   1 root root     29 2008-11-28 03:08 vmlinuz -> boot/vmlinuz-2.6.27-9-generic
lrwxrwxrwx   1 root root     29 2008-10-31 12:59 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
drwxr-sr-x   7 1000  1000  4096 2002-07-16 02:33 zsnes-1.36

```

It's seeing the hard drive now, but I attempted to boot off the HD, and it still just says 'GRUB'.

I ran 'sudo fsck -yCM /dev/sda1' again, and here was the output:

```
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1: clean, 655995/14286848 files, 20374025/28553521 blocks

```

---

### Post by caljohnsmith on 2009-01-28
Great, it looks like your sda1 partition is not lost after all. How about doing:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of the commands before typing "quit." Then reboot, and let me know exactly what happens.

---

### Post by Tuxoid on 2009-01-28
grub's output:

```
 root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by Tuxoid on 2009-01-28
my system successfully booted :popcorn:

---

### Post by Tuxoid on 2009-01-28
thank you very, very much.

I don't have to disregard a years worth of my artwork.

I'd mark this thread as solved, but I don't know how with the new setup on the forums.

---

### Post by caljohnsmith on 2009-01-29
That's great news, glad it's all working again. Cheers and have fun with your artwork. :)

---

