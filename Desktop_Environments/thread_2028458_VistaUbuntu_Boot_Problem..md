---
title: "Vista/Ubuntu Boot Problem."
date: 2012-07-18
forum: Desktop Environments
---

### Post by pras9744 on 2012-07-18
After installing Ubuntu after Vista, am not able to see boot screen and boot menu. it directly boots from Vista - and not even showing me the boot options.


Here is the boot repair info 

[http://paste.ubuntu.com/1098142/](http://paste.ubuntu.com/1098142/)


note: after boot repair was done, before the system starts booting - after the memory check etc., - the screen flashes for a second and gives "monitor frequency out of range " (as if no signal to the monitor)  and starts with Vista boot in couple of seconds... 

please help.

---

### Post by ikt on 2012-07-18
try grub-update from livecd?

---

### Post by oldfred on 2012-07-18
Since you have multiple drives, which drive are you booting from with BIOS?

You should have newest grub in sda and Windows in sdb (so if you want to directly boot Windows from BIOS your could, but normally would not need to).

You also have installed grub2's boot loader to NTFS partitions sda1 & sda2. All NTFS partitions have to have a NTFS boot sector even if not booting. If only installed once you can recover the NTFS sector with testdisk or rebuild a generic NTFS partition boot sector. 

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

Or:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by pras9744 on 2012-07-19
am still not able to see the bootup menu. 
it direclty boots to Vista. 
 
the screen flashes for a second ( as if there it displayed something) but nothing on the screen again ( and i get a "no signal" in the monitor). 
then after 10 seconds ( which i think is the wait time for the boot menu, it boots automatically to vista. 
 
is it possible that the grub does not recognize the monitor/display correctly and not able to show the menu l????

---

### Post by YannBuntu on 2012-07-19
Hello
> **pras9744 said:**
> the screen flashes for a second and gives "monitor frequency out of range " (as if no signal to the monitor)

Please run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the **"out-of-range"** option, apply. Reboot and tell us what you observe.

---

### Post by pras9744 on 2012-07-19
> **YannBuntu said:**
> Hello


Please run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the **"out-of-range"** option, apply. Reboot and tell us what you observe.

YES it worked.  THANK YOU VERY MUCH.

---

### Post by YannBuntu on 2012-07-19
You're welcome. Please use the "Thread tools" at the top of this page to mark this thread as [Solved].

---

