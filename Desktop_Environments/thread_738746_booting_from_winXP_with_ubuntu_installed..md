---
title: "booting from winXP with ubuntu installed."
date: 2008-03-28
forum: Desktop Environments
---

### Post by mlopres on 2008-03-28
I recently removed windows from my system, and decided to go with Ubuntu. However, I decided the other day I'd like to keep ubuntu and create a new partition and throw XP back on my laptop and have a Dual boot.

The problem is everytime i try to boot from a windows CD to start the installation it just stalls out and does nothing. I've tried two different XP CD's and I get the same thing. It attempts to boot from the CD, then I just get a black screen with cursor flashing.

I've ensured that booting from CD is enabled through my BIOS and i've created a NTFS partition within Ubuntu already to install XP on. I'm just not sure why I can't boot any XP cd now. It seems that Ubuntu did something.

---

### Post by warp99 on 2008-03-29
Microsoft will not let you install their OS on a separate partition after Ubuntu is installed. XP will overwrite the Ubuntu boot loader (Grub) and take over the entire hard drive. When people say that Microsoft does not play nice with others this is what they mean. :(

The only way is to wipe the drive, install XP, then re-install Ubuntu. If your laptop has enough power you could install XP in Vmware or VirtualBox so you have access to XP, but the virtual image may have some limitations when using things like DirectX. It all depends on the machine you're using.

---

