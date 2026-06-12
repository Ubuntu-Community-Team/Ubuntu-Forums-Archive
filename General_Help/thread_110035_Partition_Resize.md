---
title: "Partition Resize"
date: 2005-12-29
forum: General Help
---

### Post by OlineSixtyOne on 2005-12-29
I have a big 100+GB NTFS Windows partition on my 120GB hard drive. This is my only hard drive, so my Ubuntu partition is tiny. Is there anyway to resize my Windows partition so I could add a FAT32 partition and reinstall Ubuntu on a larger partition?

---

### Post by OlineSixtyOne on 2005-12-30
bump

---

### Post by bonzodog on 2005-12-30
Boot windows -- defrag the disc.
Back into linux, and:

sudo apt-get install gparted

I believe gparted will be able to resize the windows partition for you, and you can use it to create the new fat 32 and new linux ext3 or reiserfs partitions.

---

### Post by OlineSixtyOne on 2005-12-30
Gparted says that it cannot resize NTFS partitions. Thanks anyway. I feel a Windows reinstall coming up...

---

### Post by plors on 2005-12-30
Did you install the necessary plugin for ntfs? (check also menu: GParted ->Filesystems)
if not, you need to install ntfsprogs. gparted will detect and use them.

cheers

---

### Post by OlineSixtyOne on 2005-12-31
After installing ntfsprogs, I resized with gparted, after the resize was done (100GB to 60GB), gparted told me it was still 100GB. I rebooted and tried again, same problem. I set it up to resize then fill the space with an ext3 partition, but it failed because it didn't actually resize the ntfs partition. What is going on?

---

### Post by plors on 2005-12-31
this is a known issue. Could you please try this again with the latest gparted/libparted? Or, more conveniently, download the [livecd]("http://gparted.sourceforge.net/livecd.php") and resize from there.

cheers

---

### Post by OlineSixtyOne on 2006-01-01
My last attempt was with the latest version. It's late, so I'll give the Live CD a shot tomorrow. Thanks for the help.

---

### Post by OlineSixtyOne on 2006-01-01
Oh well, my 52x CDROM drive just quit on me, so now I have to wait for NewEgg to ship a new one. My PX-740A has never worked with the Ubuntu CDs, because there are failures when loading packages and stuff. This has happened on both of my PX-740A's, and on all the firmwares I have tried.

Of course this means no attempt with the Live CD for a while.

---

### Post by Omnios on 2006-01-01
I remeber someone telling me that the ntfs partition can not be moutned by linux when you try to resize and partition it, dont think its the hole drive though. You defiantly need the ntfs plug in for Qt parted as it needs it to resize and partition ntfs.

---

### Post by Luke771 on 2006-01-01
I wouldn't attempt anything other then reading on NTFS partitions using Linux based software. I use a Partition Magic bootable CD, which is commercial, but there are some free alternatives on the net. That's the easyest and safest way to resize partitions (Yes you still want to back up your data before you start)

---

### Post by akniss on 2006-01-01
I've never had problems resizing NTFS partitions with the Breezy install disk.  I've reduced the size of the default Windows partition on three laptops in the last two months with no trouble.  Just make sure you defrag windows before you do it.

---

### Post by OlineSixtyOne on 2006-01-06
The Live CD produced the same error I got using the installed OS. I set it up to shrink Windows and then fill the extra space with a new ext3 partition. The creation of the new partition fails, because the Windows partition is not resized and there isn't any room. This is on a SATA hard drive. It is the only drive in the computer. Any other ideas?

---

### Post by OlineSixtyOne on 2006-01-07
Allright. I finally used a Knoppix boot disc to succesfully shrink my Windows Patition to 60GB, leaving about 40GB of free space. I think I'll just mount it was /stor/ or something.

---

