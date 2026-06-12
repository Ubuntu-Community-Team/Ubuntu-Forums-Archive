---
title: "Live CD boots to command prompt."
date: 2009-02-23
forum: General Help
---

### Post by KilledXDestiny on 2009-02-23
I've just finished my first build and want to install Ubuntu 8.04. The computer boots the CD but when I try to use it (without install to check if everything works) it loads for a while before going to a blank command prompt with the title "BusyBox V1.1.3"

I've tried using startx but the command isn't recognized.

If it's helpful here are my specs:
CPU: Intel Core2 Quad Q8200
Motherboard: Gigabyte GA-EP45-UD3R
PSU: Corsair HX-620
Graphics Card: Galaxy GeForce 9800GT 512MB
Wireless Network Card: D-Link DWA-556 Xtreme N Wireless
Optical Drive: Samsung SH-S223F SATA DVDRW
RAM: OCZ PC2-8500 Reaper HPC (4GB, DDR2)

Any help would be greatly appreciated. 
Thanks

---

### Post by taurus on 2009-02-23
Did you burn the CD yourself?  If you were, you need to take these steps:

1.  run a checksum to check the integrity of the ISO image right after you've download it,

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  burn it at a slow speed like 4x,

3.  and at the initial menu from the LiveCD, run check cd for defects option to make sure the CD is good.

---

### Post by KilledXDestiny on 2009-02-23
The CD is good, I've run integrity checks and already used it to install on my laptop.

Would it be worth checking the disc again?

Edit: I just tried a defect check...ended up at the same command prompt.

---

### Post by Dustin2128 on 2009-02-23
I have the exact same problem, fix please?

---

### Post by KilledXDestiny on 2009-02-23
I've fixed it (YAY!!)
It's a BIOS issue; I read about another board that had problems as the SATA drives were set to IDE so I decided to try it on my board. 
Glorious Ubuntu Desktop!!
Just go into BIOS find where your drive settings are (mine is under "Integrated Peripherals") then set the SATA drives to AHCI. In mine I had to both change the "Onboard SATA/IDE Ctrl Mode" from IDE to AHCI and also change "SATA RAID/AHCI Mode" from Disabled to AHCI.

So happy ^_^

---

