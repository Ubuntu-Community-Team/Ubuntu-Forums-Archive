---
title: "Dell C600 Laptop + Ubuntu = Hard Drive lockups"
date: 2009-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Spaz007 on 2009-03-23
For the past few months I been using OpenSUSE for Linux on my old C600. I been wanting to try Ubuntu and decided to go ahead. The install went great and Ubuntu quickly found my wireless card and my network printer without needing me to install any drivers. Just that alone was a jump up from SUSE because it didn't find anything for you. But after just 15 min I started having issues with my hard drive randomly clicking over and over. I turned off my PC and then booted back up to see that the drive was so messed up that fsck couldn't fix the drive. I installed Ubuntu again to only see the same thing happen a few minutes after booting. I since reinstalled SUSE and had no issues for a solid 12 hours now.

Has anyone see a issue like this? I'm thinking of trying 8.04 and seeing if the problem is still there.

---

### Post by Spaz007 on 2009-03-24
If Ubuntu can't work correctly on a old standard like EIDE correctly then I'm moving on. This is a bit embarrassing for a so called mature distro. I will just move back to a usable Linux distro like Fedora or SUSE.

---

### Post by mpsii on 2009-03-24
I have not seen/heard of this kind of issue with Ubuntu. Couple of questions:

1) Which version of Ubuntu? 8.10 (Intrepid) is the latest release
2) What file system? (ext2, ext3, etc)
3) What kernel version?

---

### Post by Spaz007 on 2009-03-24
1: Tried 8.10 and 8.04 and also Xubuntu 8.10

2: Ext3

3: 8.10 is 2.6.27

---

### Post by Spaz007 on 2009-03-25
Just seen something new. As long as I don't log into the PC the hard drive doesn't start clicking and locking up. So something starts and kills the drive. New hardware checks at startup maybe?

---

### Post by Spaz007 on 2009-03-27
OK, I found the fix for my issue. Its not a bug but a swap area size issue. Being on the border line min required to run Ubuntu at 256 MB I found I need a larger swap area. I first noticed that when I installed OpenSUSE the swap area it setups by default is 2 GB. The default Ubuntu setup was 512 MB. I wasn't really sure at the time if it would fix anything but I installed 7.10 using a swap area of 3 GB and the OS never locked up. I have since upgraded the OS to 8.10 and its still running stable.

---

### Post by wandalalakers on 2009-04-07
You might be better off with Xubuntu if you only have 256mb.

---

