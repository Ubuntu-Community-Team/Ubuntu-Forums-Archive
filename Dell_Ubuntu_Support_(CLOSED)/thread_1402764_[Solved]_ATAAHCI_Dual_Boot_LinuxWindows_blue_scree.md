---
title: "[Solved] ATA/AHCI Dual Boot Linux/Windows blue screen of death"
date: 2010-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by K_Boomer on 2010-02-09
Are you getting the Microsoft infamous blue screen of death when trying to dual boot or install windows? 

I spent several hours trying to dual boot windows XP off of crunchbang, and I finally found the solution for me. I will post what my problem and solution were, and hopefully I can help some poor soul temporarily tame the devil that is Windows.

I am running an Inspiron 1545 laptop with a new western digital harddrive.

I was following this tutorial:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1")

My problem: Any time I tried to boot windows xp off of the disk, I was greeted first with the blue screen of death. Thinking it was a format problem, I tried altering partitions with GParted/fdisk, in several ways.

1) 10GB unallocated partition for Windows
2) 10GB FAT32 partition for windows
3) 10GB NTFS partition for windows
4) entire blank partition for windows
5) entire FAT32, and entire NTFS for windows

I tried checking disk errors, but the disk seemed fine

Nothing worked. I still got the blue screen harddrive error when trying to boot windows xp off the disk.

**Solution for me: **

Windows hates AHCI and likes ATA.

After ensuring EVERYTHING you want on your operating system is backed up, go into your BIOS setting and switch AHCI to ATA. 

Restart and boot off Windows disk.

-Hope your problem and solution were as simple as mine.
Good Luck

---

