---
title: "How can I triple boot?"
date: 2016-11-30
forum: Debian
---

### Post by yodayams on 2016-11-30
I currently have Ubuntu 16.04 LTS installed alongside Windows 7. So when I boot I can select either Ubuntu or Windows. My problem is that I want to also install Debian Linux in a triple boot. How can I shrink my Ubuntu partition (it's 250gb I want to make it 125gb) so I have room to install Debian? And how do I setup a triple boot? When I install Debian will it automatically configure GRUB to triple boot Ubuntu and Windows?

---

### Post by howefield on 2016-11-30
Thread moved to the "*Debian*" forum.

---

### Post by oldfred on 2016-11-30
I have multiple Ubuntu installs.
Generally last installed system, takes over booting, but you can control that and I would expect Debian's grub2 to work like Ubuntu's and offer to boot all systems.

If Windows 7, then you probably are BIOS/MBR with 4 primary partition limit. Is Ubuntu in the extended partition as a logical partition? If so then you should have no issues creating additional logical partition(s).
If not hibernating, you can use same swap for both installs.

You may want a shared data partition or two. When I had XP I used a shared NTFS data partition. But as I installed more Ubuntu versions, and used XP less added a /mnt/data partition. When I retired XP all my shared data go moved into the shared Linux formatted partition.
Because most of my data is in my data partition, I keep / (root) at 25GB or so, and use about 10 to 15 GB including /home. New install is a lot less & I try to houseclean but it manages to grow until next LTS install.

---

### Post by palopdsthsa on 2017-04-26
The best way it would be to have 2 disks, one for Linux/Debian/Ubuntu and 1 for Windows, but as long as you have only one you can install Debian with any problem, Grub2 will do everything for you and when you'll boot the pc you'll get a prompt to chose where you want go. I had it, but I have chosen to divide the security in 3 disks, one for every system.

---

