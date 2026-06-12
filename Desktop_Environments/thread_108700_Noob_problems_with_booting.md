---
title: "Noob problems with booting"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Barry0551 on 2005-12-26
I am so new to Linux and especially Ubuntu that I feel like a kid with a new high tech toy.  Here is my problem...I have win xp pro on one partition of my one hd.  All partitions are ntfs except two that are fat32 with the xp on it.  I now have an (ext3?) partition for Ubuntu and everything worked fine until I was in win and installed a musicmatch software.  The linux partition does not show up at all in windows.  I now cannot boot into linux at all.  I get the bin/sh: can't access tty; job control turned off error.   I tried the instructions about restoring grub, but either I did it wrong or I have bigger problems. Also tried the live cd approach but I am lost.  I am sick of the windows scene, and will be grateful for some help.  Thanks, from a real newb.

---

### Post by kenweill on 2005-12-26
[QUOTE=Barry0551]I am so new to Linux and especially Ubuntu that I feel like a kid with a new high tech toy.  Here is my problem...I have win xp pro on one partition of my one hd.  All partitions are ntfs except two that are fat32 with the xp on it.  I now have an (ext3?) partition for Ubuntu and everything worked fine until I was in win and installed a musicmatch software.  The linux partition does not show up at all in windows.  I now cannot boot into linux at all.  I get the bin/sh: can't access tty; job control turned off error.   I tried the instructions about restoring grub, but either I did it wrong or I have bigger problems. Also tried the live cd approach but I am lost.  I am sick of the windows scene, and will be grateful for some help.  Thanks, from a real newb.[/QUOTE]

I don't actually get it. Can you be more specific?

---

### Post by jbraum on 2005-12-28
I'm having a similar problem when booting.  I've been up and running for a couple of months then this problem appeared.  Here's what I'm seeing on boot.

Loading, please wait...
FATAL:  module unknown not found.
mount:  Mounting /dev/hdb1 on /root failed:  No such device
mount:  Mounting /root/dev on /dev/ .static/dev failed:  No such file or directory
mount:  Mounting /dev on /root/dev failed:  No such file or directory
Target filesysetm doesn't have /sbin/init

BusyBox v1.00-pre10 (Debain 20040623-1ubuntu22)  Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh:  can't access tty;  job control tuned off

Any suggestions

---

### Post by art on 2005-12-28
EDIT
nevermind...

---

