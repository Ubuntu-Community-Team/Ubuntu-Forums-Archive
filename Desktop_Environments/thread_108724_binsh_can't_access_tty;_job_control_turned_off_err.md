---
title: "bin/sh: can't access tty; job control turned off error"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Barry0551 on 2005-12-26
I am  new to Linux and especially Ubuntu.  Here is my problem...I have win xp pro on one partition of my one hd. All partitions are ntfs except two that are fat32 with the xp on it. I now have an (ext3?) partition for Ubuntu and everything worked fine until I was in win and installed a musicmatch software. The linux partition does not show up at all in windows. I now cannot boot into linux at all. I get the bin/sh: can't access tty; job control turned off error. I tried the instructions about restoring grub, but either I did it wrong or I have bigger problems. Also tried the live cd approach but I am lost. I am sick of the windows scene, and will be grateful for some help. Thanks, from a real newb.

---

### Post by ninotob on 2005-12-26
I don't know anything about this particular error, but if windows somehow wrote to ext3 partition (though how it would have I don't know), it could have hosed the ext3 partition.

Here's what I would do first, I would verify that the linux partition is still good by booting from a live cd, then mounting the drive.  If you can't mount it, it's probably been tainted somehow.  If you can, it may be worthwhile to continue troubleshooting it (depends on how much time and data you have invested in the linux install).

---

