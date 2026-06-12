---
title: "Severely messed up partition table after windows 7 dual boot install failed"
date: 2009-08-07
forum: Desktop Environments
---

### Post by xbunti on 2009-08-07
I followed the steps in ubuntu forums to install windows 7
to dual boot into a pc which already had ubuntu 9 running in it.

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

(more detailed steps given in [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999) )

I had ubuntu 9 already installed in my pc with one 750gb HD
which had about 7 partitions with ubunto OS installed in
the first 100GB partition which was primary.

I shrunk the ubuntu primary partition from 100gb to 50gb and
the set the 50gb freed up as NTFS.

Then I put in windows 7 dvd and rebooted and went past first 3 screens
and in the screen to choose the partition to install windows I chose
the new 50gb ntfs partition i had created above and clicked next button.

The windows 7 install kept spinning for over 2 hours and
the only way I could get out of it was to use reset button in my pc.

I removed windows dvd and rebooted and found ubuntu works fine and
all my ubuntu files seem to be there.

However, my HD partion table seems to be completely messed up !!

Before the windows7 install attempt my fdisk used to show :

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bf9d

Device Boot Start End Blocks Id System
/dev/sda1 1 6086 48885763+ 83 Linux
/dev/sda2 * 6087 11185 40957717+ 7 HPFS/NTFS
/dev/sda3 11186 91201 642728520 5 Extended
/dev/sda5 11186 12181 8000338+ 82 Linux swap / Solaris
/dev/sda6 12182 30413 146448508+ 83 Linux
/dev/sda7 30414 78453 385881268+ 83 Linux
/dev/sda8 12182 30413 146448508+ 83 Linux

and now it shows :

Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bf9d

Device Boot Start End Blocks Id System
/dev/sda1 1 6086 48885763+ 83 Linux
/dev/sda2 * 6087 11185 40957717+ 7 HPFS/NTFS
/dev/sda3 11186 91201 642728520 5 Extended
/dev/sda5 11186 12181 8000338+ 82 Linux swap / Solaris
/dev/sda6 12182 30413 146448508+ 83 Linux
/dev/sda7 30414 78453 385881268+ 83 Linux
/dev/sda8 12182 30413 146448508+ 83 Linux
/dev/sda9 30414 78453 385881268+ 83 Linux
/dev/sda10 12182 30413 146448508+ 83 Linux
/dev/sda11 30414 78453 385881268+ 83 Linux
/dev/sda12 12182 30413 146448508+ 83 Linux
/dev/sda13 30414 78453 385881268+ 83 Linux
/dev/sda14 12182 30413 146448508+ 83 Linux
/dev/sda15 30414 78453 385881268+ 83 Linux
/dev/sda16 12182 30413 146448508+ 83 Linux
/dev/sda17 30414 78453 385881268+ 83 Linux
/dev/sda18 12182 30413 146448508+ 83 Linux
/dev/sda19 30414 78453 385881268+ 83 Linux
/dev/sda20 12182 30413 146448508+ 83 Linux
...............................
................................
...............................
/dev/sda59 30414 78453 385881268+ 83 Linux
/dev/sda60 12182 30413 146448508+ 83 Linux

and gparted shows /dev/sda with just one partition for who disk
and in its drop down list of drives it shows the list
/dev/sda then /dev/sda100, sda101, sda102...... etc... to /dev/sda255
and no entries between /dev/sda1 to /dev/sda99

How can I fix this messed up partion info ??
Please help !!

If this portends what windows 7 is to be then it seems pretty grim
not to mention it failed to install.

---

### Post by ajgreeny on 2009-08-07
You say that before the windows install you got this error message from fdisk -l
```
Warning: omitting partitions after #60.
They will be deleted if you save this partition table.
```Is that right.  If so there appears to have been something wrong with the partition table before you installed Windows 7.  The output shows that you have 7 partitions, sda 1, 2, 3, 5, 6, 7, and 8.  However if you look closely you will see that sda6 and sda8 appear to use the same space on the disk.  After installing Windows & the same problem is still there with all of these
```
/dev/sda6 12182 30413 146448508+ 83 Linux
/dev/sda7 30414 78453 385881268+ 83 Linux
/dev/sda8 12182 30413 146448508+ 83 Linux
/dev/sda9 30414 78453 385881268+ 83 Linux
/dev/sda10 12182 30413 146448508+ 83 Linux
/dev/sda11 30414 78453 385881268+ 83 Linux
/dev/sda12 12182 30413 146448508+ 83 Linux
/dev/sda13 30414 78453 385881268+ 83 Linux
/dev/sda14 12182 30413 146448508+ 83 Linux
/dev/sda15 30414 78453 385881268+ 83 Linux
/dev/sda16 12182 30413 146448508+ 83 Linux
/dev/sda17 30414 78453 385881268+ 83 Linux
/dev/sda18 12182 30413 146448508+ 83 Linux
/dev/sda19 30414 78453 385881268+ 83 Linux
/dev/sda20 12182 30413 146448508+ 83 Linux
...............................
................................
...............................
/dev/sda59 30414 78453 385881268+ 83 Linux
/dev/sda60 12182 30413 146448508+ 83 Linux
```being alternate duplicates.

I have never seen this before and admit to being completely baffled about what might cause it.  However to be fair to Windows 7, it would appear that this is not a problem related solely to its installation process, but perhaps windows being totally baffled, as I am, about your partition table into which it was trying to install.

I think I would make sure that all my files in Ubuntu are fully backed up, then using gparted, or fdisk if you are content with the command line, delete all partitions that are not actually an integral part of the ubuntu install, eg if you have a separate /home partition, leave that.  Then I would try installing windows again into a hopefully cleaner partition setup.

Let us know what you eventually do, and the outcome, but it really is a weird situation.

---

### Post by xbunti on 2009-08-07
Sorry - I mistyped earlier :

The message : 

Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

was only after trying to install windows 7.

Before installing windows 7 fdisk did not report any warnings.

I have edited my original post to correct this typo.

Also the only minor issue I can think of is that my ubuntu 9 was 32bit (but running on intel Q6600 ie. 64bit cpu)
while the windows 7 RC DVD I tried to install was 64bit version
- I dont think that should matter at all but who knows with windows.

---

### Post by ajgreeny on 2009-08-07
OK, I see your error was not a pre-windows problem, but I presume the duplication of sda6 and sda8 was still reported in the fdisk output.  If so, you did still have a problem before windows was installed.  This is part of the output you included in your post, note the start, end, and block numbers are identical for sda6 and sda8; impossible, I think.
```
/dev/sda6 12182 30413 146448508+ 83 Linux
/dev/sda7 30414 78453 385881268+ 83 Linux
/dev/sda8 12182 30413 146448508+ 83 Linux
```

---

