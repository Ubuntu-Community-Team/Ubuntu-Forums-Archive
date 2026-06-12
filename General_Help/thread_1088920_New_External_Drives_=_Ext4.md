---
title: "New External Drives = Ext4?"
date: 2009-03-06
forum: General Help
---

### Post by CarlosinFL on 2009-03-06
I have two new external USB drives I will be using for backup / RAID. I just created the partition table on them using 'fdisk' and now when I was going to format the drives, I noticed I had an option to use Ext4. I was wondering how safe this new file system is for an external USB hard drive? I know its new and I have always used Ext3 for years. Can anyone tell me if this is a good or bad idea?

---

### Post by Skripka on 2009-03-06
Ext 4 handles drive checks MANY times faster than ext3, it also is in general much faster than ext3 IME.  BUT, it seems much more sensitive to being mounted/unmounted improperly-resulting in some corrupted data.

My root and /home partitions are ext4 on my Arch box here-and I've had unclean restarts that resulted in corrupted config files that were still open.  I still run it, on my drives in my tower and haven't lost any actual data apart from a few config files resetting themselves....but a USB drive I'd sooner ext3 it, at this point in time.

---

### Post by CarlosinFL on 2009-03-06
Thanks for the heads up. Just wondering if its possible to install 8.10 Ubuntu with / partitions as Ext4? Is that option available in the installer or is there an upgrade option post install?

---

### Post by Skripka on 2009-03-06
> **Carlwill said:**
> Thanks for the heads up. Just wondering if its possible to install 8.10 Ubuntu with / partitions as Ext4? Is that option available in the installer or is there an upgrade option post install?

Ext4 cannot be used for an Ibex install at this time, within my knowledge.  GRUB needs patches applied to run it (Even GRUB 2.0 in development doesn't actually support it without patches)-and you need a new enough kernel that supports it too.  We archers done both ourselves and can run it, because we like being free to live dangerously.

I think Ext4 might be supported by Jaunty-but I'm unsure of Canonical's timetables since I don't use Ubuntu anymore.

Also, from what I gather and remember you can upgrade an ext3 partition to an ext4 partition-if you want to down the line.

---

### Post by Xbehave on 2009-03-06
I think (going on what ive seen not what ive done) that / can be ext4dev (ext4 in jaunty) but that grub needs patching for /boot to be there, so if you have a seperate boot you can use ext4 on ibex.

---

### Post by bodhi.zazen on 2009-03-06
ext4 is considered stable and is available in 9.04 Alpha.

It may be the default in Fedora 11

My advice, use the disk as ext3 until you upgrade your distro, then convert ext3 to ext4 ;)

---

### Post by CarlosinFL on 2009-03-09
Are you guys saying that I ca't even format a external USB drive with Ext4 right now and mount it to my 8.10 system which is using Ext3?

I am guessing the 8.10 system can't even mount any Ext4 file systems and that is why I received the error you see below...

I find it strange I can format an Ext4 system from a machine that does not support it in any kind of way...

---

### Post by bodhi.zazen on 2009-03-09
One consideration with any file system is of compatibility. This is one reason FAT, and now ntfs are so popular.

ext4 is new and even with Ubuntu 9.04 and Fedora 11 (both in alpha right now) not all of the features are yet available.

If you want to use ext4 and you do not wish to use an alpha release, you will need to :

[http://ubuntuforums.org/showthread.php?t=973701](http://ubuntuforums.org/showthread.php?t=973701)

I have used this how to with success. However, there are reports of data loss on Ubuntu using ext4 .

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

See also:

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

My advice is that you wait to use ext4, but if you must take the time to look at the above links ;)

---

