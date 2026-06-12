---
title: "How do I move the start of my ext3 partition?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by Schalken on 2006-08-26
Because of all the games I install in Windows, my little 20GB NTFS partition is fast running out of space (and I haven't even filled the desktop with games yet!) while my 60GB Ubuntu partition still has a good 13GB free.

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=14874&stc=1&d=1156589547[/IMG]

The problem is GParted doesn't let me to move the *start* of my ext3 (Ubuntu) partition, only the end of it, making Windows stuck in it's tiny little 20GB area with no room to move.

How can I resize my ext3 (Ubuntu) partition to give more room to the NTFS (Windows) partition that is before it?

---

### Post by Ramses de Norre on 2006-08-26
I'm afraid this is impossible.. As far as I know you can't move the start of an ext3 partition, only way around for you would be tarring the ext3, saving the tarball somewhere, deleting old and making new partition with other position, untarring the tarball to the new partition.

---

### Post by Schalken on 2006-08-26
how much space would I need to free if I was to gzip my 30GB home directory and put it on the NTFS drive?

---

### Post by Schalken on 2006-08-28
BUMP. I'm just looking for an estimate, my computer doesn't have the power to Gzip such huge files to accurately test out how much it can compress.

---

### Post by twosox on 2006-08-28
Okay, this is my first post, but I think I have a pretty good solution for this problem.

I have been using Boot It Next Generation (BING) from Terabyte Unlimited ([http://www.terabyteunlimited.com](http://www.terabyteunlimited.com)) for a while to do all the things that Partition Magic can do, for a lot less money.  Also, you can download a copy to try it out if you want.  Now that I'm on Ubuntu as my primary OS, I have been using grub as the bootloader, but the partition stuff in BING is first-rate.

You have to "slide" the partition to the beginning of the drive -- it may give you a warning about backing up, so I would consider your options there.  I've never lost any data (as near as I can tell), but you never know...

Then I used gparted from the Ubuntu Live CD and expanded the ext3 filesystem (BING suggested this as well, as it does not have Native Linux formatting).

Finally, I ran [e2fsck and resize2fs]("http://www.ubuntuforums.org/showthread.php?t=232925&highlight=resizefs2") to get the partition for the full size of the hard drive.

Hope that helps.  These forums are a big part of why I've switched.

Thanks!

---

