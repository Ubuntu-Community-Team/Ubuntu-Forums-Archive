---
title: "Installation problems"
date: 2005-07-03
forum: Desktop Environments
---

### Post by NeoRevan on 2005-07-03
I am trying to install this OS from a Install/Live DVD, but I have had a worldload of problems.
[list=1]
[*]Installer hung before it even started
Solution: I searched around the forums and google, and found how to disable SATA so the install could load
[*]Install hung at Configuring DHCP
Solution: Install with a special parameter that disabled DHCP config
[*]Install hung at what WOULD be the Configuring DHCP menu
Solution: Install in Expert mode and skip this altogether
[*]Install couldn't install Grub boot loader
[/list]
Now the last problem is the outstanding one. It gets to about 50 % then fails with a Fatal Error. I tried installing everywhere, even onto a floppy, but it fails with the same damn Fatal Error.
I should tell you, Im gonna dual boot it with WinXP and I would prefer it if that was still possible, unlike with FC3 when my MBR got damaged and left me facing a reformat of Windows drive.

---

### Post by mtron on 2005-07-03
Hi neo! 

On what hardware do you want to install ubuntu? 

did you look at the special boot options? 

Is your Router set to automatic DHCP IP assignment? 

Did you disable the virus or boot sector protection in the bios? 

Please give us some more information and we will try to help you! Btw: you do not need to reinstall windows to reset your master boot record. see [this](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)  article from microsoft, or download a windows98 bootdisk and run "fdisk /mbr" (yes it works also with windows xp)

---

### Post by NeoRevan on 2005-07-03
Ya sorry for the lack of info, I ment to add it. No, seriously. I did. 

[list]
[*]**_*Motherboard:*_** Intel Culver City D925XCV Socket 775
[*]**_*CPU:*_** Intel Pentium 4E, 3200 MHz (16 x 200) 1 MB L2 Cache, Prescott
[*]**_*RAM:*_** 4x Crucial DDR-2 512 MB CL3 SDRAM
[*]**_*Graphics:*_** nVIDIA GeForce 6800 PCI-E (256 MB)
[*]**_*Storage:*_** 2x Maxtor 6B300S0 (300 GB, 7200 RPM, Serial-ATA/150), RAID0
[*]**_*Reader:*_** Lite-On DVD SOHD-167T, 16x DVD/48x CD
[*]**_*Writer:*_** NEC 2500A DVD-/+RW (Patched to Dual Layer), DVD+RW:8x/4x, DVD-RW:8x/4x, DVD-ROM:12x, CD:32x/16x/40x
[*]**_*Network Adapter:*_** Marvell Yukon 88E8050 PCI-E ASF Gigabit Ethernet Controller
[*]**_*Sound:*_** Realtek HD Audio rear output
[*]**_*Monitor:*_** Samsung SyncMaster 710v
[*]**_*Resolution:*_** 1280x1024 @ 72Hz
[/list]

I can't remember if I looked at special boot options, I hit F1 for the help which is how I learned of the Expert install mode, and I looked through pretty much everything there.

My router is DI-604 and on the paper it can assign DHCP, but I was having trouble with this function, so I set it manually in Windows IPConfig.

Im not sure if my BIOS has those settings, but I'll take a peek around tomorrow. Right now its 1:30 am, and my eyes are slowly growing shut  :razz: 


Thanks :)
EDIT: Hm, it might help if I turned DHCP back on in my router  :oops: 
I'll try again tomorrow.

---

### Post by NeoRevan on 2005-07-04
Well I can't find any boot sector protection setting in my bios, so any other way to install the bootloader?

---

