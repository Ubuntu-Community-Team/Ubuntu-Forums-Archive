---
title: "Windows XP Pro on Dell E310"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by a.webster on 2011-10-15
I am going to buy a 1tb hard drive for my dell tomorrow and can I partition 500gb to windows and then install the other 500gb to ubuntu, or should I install all 1000gb to windows xp pro. I am going to download the windows installer option when I install ubuntu.

---

### Post by Kai Summers on 2011-10-15
When you do the Ubuntu install you will be asked if you would like to keep windows, if you opt to keep windows then you will be able to partition the drive so that you have 500GB for both windows and 500GB for Ubuntu, the installer will take care of reallocating the drive for you and creating the disk tree...

Good luck and enjoy!

---

### Post by varunendra on 2011-10-17
> **a.webster said:**
> I am going to download the windows installer option when I install ubuntu.
You mean a WUBI install (Ubuntu 'inside' windows), right? That will have a 30 GB partition size limitation + a few more for ubuntu. If there are any workarounds to exceed that limit, I'm not aware of it. But regardless, I won't suggest a WUBI install. It is meant for those who already have a windows install and they want to 'test' Ubuntu safely. But since you are going to make a fresh installation of windows as well, it is best to install both windows and Ubuntu in their own partitions independently. This will ensure you have full performance of Ubuntu and no WUBI-specific limits.

The best procedure and 'my preferred' plan (only for a dual boot system) would be:

[LIST]
[*]boot from XP cd
[*]create a 40 to 60 GB partition for XP (or more if your use of it demands so).
[*]create two equal size ntfs partitions in the remaining space (leaving at least 40 Gb or more space for Ubuntu).
[*]Finish installing XP in 1st partition. You can format the other two partitions later.
[*]Boot from Ubuntu CD into live session.
[*]Run Gparted and create a 'Logical partition' with ext4 file system, and a 2GB swap partition in the remaining space.
[*]Install Ubuntu in the ext4 partition, and done!
[/LIST]
Some of us here prefer a separate /home partition, but that's entirely a matter of preference and what you are going to do with your installation. It generally doesn't matter, but a little bit of research on it to see whether it suits you won't hurt. :)

---

