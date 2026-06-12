---
title: "WindowXP/Linux Dual-Boot on Dell Dimension 3000"
date: 2007-04-07
forum: Desktop Environments
---

### Post by ltcmdrdata on 2007-04-07
I just installed Ubuntu on my Dell Desktop. Originally my computer had 3 primary partitions (/dev/hd1a ~ 47MB), (/dev/hd2a ~ 145GB), (/dev/hd2a ~ 3GB). I read somewhere that the third partition was only used for system restore, so I used that for the swap and split the 145GB into two (115GB and 30GB). So now I had 4 partitions, the first two (47MB,115GB) for WindowsXP and then the last two (30GB,3GB) for Linux. The installer asked me where to install GRUB and I installed it to /dev/hd2a (which is the 115GB partition that contains WindowsXP). I finished the installation, and when I boot up my computer, GRUB asks me which OS I want to run. When I select the Windows XP option, a screen flashes really fast saying
“Starting up…
GRUB Loading stage2...”
then it cycles back to the GRUB screen that asks me which OS I want to run. But, if I select Ubuntu everything works fine.

Anyone know how to fix this?

---

### Post by aysiu on 2007-04-07
I don't know much about Grub troubleshooting, but since no one has answered you in three hours, it couldn't hurt to just post you a couple of links you might find helpful.
[http://www.linuxforums.org/forum/suse-linux-help/63296-suse-10-1-windows-xp-dual-boot.html](http://www.linuxforums.org/forum/suse-linux-help/63296-suse-10-1-windows-xp-dual-boot.html)
[http://ubuntuforums.org/showthread.php?t=399616](http://ubuntuforums.org/showthread.php?t=399616)

---

