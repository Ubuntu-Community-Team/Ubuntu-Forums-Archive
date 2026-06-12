---
title: "Can't load XP after ubuntu 5.10 Install"
date: 2006-05-21
forum: Desktop Environments
---

### Post by BrianPL on 2006-05-21
Hello,

I had the ubuntu installer resize my XP NTFS partition. Ubuntu runs fine, but I can't load windows with grub. When I select Windows in the grub menu, it loads the HP rescue partition instead. This [link]("http://lwn.net/Articles/167756/") describes what seems to have happened.

Does anyone have any ideas of how I can load XP again? Did the NTFS resize damage my partition (as the link suggests)? Or could this be a problem with the order of the partitions? I seem to remember that the NTFS partition came before the rescue partition in windows.

When I modify the root line at boot time to "root (hd0,1)" it seems to recognize that its NTFS (0x07) but it stops with error 13. Details:

fdisk -l output:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1046     8399128+  1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1047       22930   175783230    7  HPFS/NTFS
/dev/sda3           22931       30094    57544830   83  Linux
/dev/sda4           30095       30401     2465977+   5  Extended
/dev/sda5           30095       30401     2465946   82  Linux swap / Solaris

menu.lst in /boot/grub:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Thanks,
Brian

---

### Post by jones_jj on 2006-05-21
The way I have always gotten Windows to play nicely with Linux is to first install Windows, and then install Linux.  You can use the Windows disk to create a few partitions and just make them all NTFS, one NTFS, and the rest FAT32 or however you like it.  Just make sure Windows is on the first partition and it is the first loaded OS.

After that you can then go ahead and install Ubuntu, and take the other partitions and let the Linux Disk Partition tool blow out the partitions and recreate them as ext3, ext2, reiser, jfs, or whatever file system you prefer.  I would suggest putting Grub in the MBR and it should be able to see both Windows and Linux just fine.

To answer your question it does sound like something to messed up when you went to mess with your Windows partition after the fact of it being installed.  There were probably files throughout the partition and when you went to resize the partition it messed up those files that may not have been at the begining of the partition.  You may want to start all over and do as I suggested.

---

### Post by roccorobb on 2006-05-24
Hey,

I'll give you my own 2 cents in a sec, but maybe it'd be more help to check out this post:

[http://www.linuxquestions.org/questions/showthread.php?t=242025](http://www.linuxquestions.org/questions/showthread.php?t=242025)

Ok, now my words:

i just did my first intstall of ubuntu and had a similar problem, with a few marked differences.  Firstly, my installation (default ubuntu installation) of the GRUB loader didn't even show XP as an option for boot.  Also, once inside linux, hda1 shows up on the desktop as mounted but is not readable (much less writable).  Finally, i had an Acronis boot loader already installed before installing ubuntu/grub.  

I was tearing my hair out for a few hours, but eventually i got it figured out.  As it turns out, my xp partition was just fine.  Yours probably is too.  From what i understand, the partitioning that occurs during install is very very safe, even though everybody will always warn everybody to backup everything first.

all i did was hit 'e' when i got the grub screen.  i erased all 4 or 5 lines there, and typed what you posted earlier in its place:

root (hd0,0)
savedefault
makeactive
chainloader +1

When i rebooted, it took me straight to the Acronis boot loader.  I would imagine that on any other machine it would boot straight to windows.

Now, my machine boots to Acronis OS Selector first.  If i choose to boot Linux, Grub comes up (after timeout) and still doesn't give me the option to boot XP, which is no longer a problem.  I suppose that doesn't help you any, but i think the problem could be fixed by adding another line to the list above -- something like savedefault or saveasdefault or something. . . i'm talking out of my butt now.

i still can't access my NTFS partition from inside ubuntu, but i'm going to follow the info on the post i sent you and see if i can't get it up and running.

hope this helps.

rje

---

### Post by razeshkale on 2007-06-29
If u have install Ubuntu on second partition?\\then there is no problem
if you want to resize partition and reinstall XP  then you have to resize your Ubuntu disk and install on Second partition and you can Restore Ubuntu Grub loader with Live CD

If you already install window, resize and recover Grub with lIve cd

---

### Post by navjeet on 2007-06-30
i have problem too with my XP SP2
actually i have download many wallpapers from [Hollywood movies wallpapers]("http://www.movieguruclub.com") site, when ever i do this my system restarts, When i checked my PC, then i got that my graphic card is not inserted properly.

---

