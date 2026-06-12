---
title: "XP recently not booting on dual boot XP/Ubuntu system."
date: 2012-05-11
forum: Desktop Environments
---

### Post by welshmike on 2012-05-11
I have a dual boot Windows XP and Ubuntu 12.04 system. The XP system will not now boot and if I try to boot it the XP logo shows but the system then boots Ubuntu. This may be as a result of me writing a file on the Desktop of the XP system from Ubuntu. 
When I use the Ubuntu Disk Utility to check the XP partition (check and repair) I get “File system is not clean”.
How may I proceed to get XP to boot please?

---

### Post by oldfred on 2012-05-11
You may need to run chkdsk or make other repairs from your  XP install disk.

But post the link to Boot-Info report that this creates.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

XP CD fixboot  - do not reinstall XP boot loader (fixMBR) unless you have the above Boot-Repair or Ubuntu liveCD as you will have to reinstall grub2 to the MBR to boot Ubuntu.
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

---

### Post by Sylslay on 2012-05-11
Boot in ubuntu and istnall Synaptic (if not in system),

Open Synaptic and re-install grub-pc,

and from terminal


sudo os-prober
sudo update-grub

---

### Post by wilee-nilee on 2012-05-11
+1 on post 2 run the chkdsk. ;)

---

### Post by welshmike on 2012-05-12
Many thanks for all the replies. 

Late yesterday I decided to start from scratch by booting Ubuntu Live USB, deleting all partitions, creating a partition table and the following partitions: fat32 for XP, ext4 for Ubuntu / and /home , a linux-swap. I planned to create an NTFS one for shared XP/Ubuntu data archive (images, videos, music, etc.) in time.
I then booted and ran XP install CD which did a BSOD Stop "0X0000007B". So I went ahead and installed Ubuntu 12.04 that I'm using now. The partitioning on my hard drive is shown below but I would like to start from scratch again with better partitioning, installing XP first then Ubuntu.

I'd very much like a step by step guide from a member of the team please.

The hard drive is SATA: Hitachi HTS545025B9A300.
Below  is the current partitioning. But I plan to set up the following partitioning: 50GB XP, 50GB ext4 Ubuntu /, 50GB ext4 Ubuntu /home, 2GB linux-swap, remainder for shared NTFS XP/Ubuntu data archive (images, videos, music, etc.)
[IMG]http://www.winchesternw.org.uk/partitioning.png[/IMG]

---

### Post by Sylslay on 2012-05-12
Before You setup new partition table, please check HDD for "bad sectors",
if any will be found than create new partition withhout "bad sectors",

IMHO, less partitions less trouble,

Just make 3 primary partition , first 100 GB NTFS, 
than 2 GB for  Swap,
and left for ex4.

---

### Post by welshmike on 2012-05-12
> **Sylslay said:**
> Before You setup new partition table, please check HDD for "bad sectors",
if any will be found than create new partition withhout "bad sectors",

IMHO, less partitions less trouble,

Just make 3 primary partition , first 100 GB NTFS, 
than 2 GB for  Swap,
and left for ex4.

What trouble might there be with the partitioning I proposed?
I understand that it is advisable to have separate / and /home partitions so that the home folder is not lost when installing new Linux distros or releases rather than upgrade.
I have found the Ubuntu community excellent over the last 4 plus years since 8.04 when I relegated Windows XP to run the few apps I needed like Atomic Mail Sender.
I had decided recently to move from Ubuntu 10.10 with the Gnome desktop to 12.04 with the Unity desktop.
Having persisted with Unity I find it a little unsatisfactory with some suprising problems and some that could be code bugs.
I'll continue with 12.04 and Unity for now. If it continues to be less than satisfactory I'll consider switching to another Linux distro; maybe Mint?

---

### Post by oldfred on 2012-05-12
I would use NTFS for XP.

Windows only installs, repairs, or boots from the primary NTFS formated (FAT may work) partition with the boot flag. Grub does not use boot flag to boot. There are a few BIOS that will not let you boot at all unless the BIOS sees a boot flag, so I suggest a boot flag on every system.

So move boot flag to sda1 and then XP should install. 

If system is newer, you may want to be sure to include SATA and AHCI drivers as part of the install.

I have a early LCD that is vertical format, so I did not like Unity using the sides. So I installed fallback or in 12.04 it is also called gnome-panel. It is almost  just like the old gnome2 but with a few changes. Some menus have moved around etc.

---

### Post by welshmike on 2012-05-13
Thanks for the tip about the boot flag.
I'm now back to a dual boot XP/Ubuntu.
I have another self inflicted problem that I post as a new thread.
(Edit) Problem solved. So I won't clutter the forum with a new thread.

---

