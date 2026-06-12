---
title: "Sharing Experience - Vostro 1200 with Ubuntu 8.10"
date: 2008-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by purba on 2008-12-23
Hi all, i just want to sharing my experience using Ubuntu 8.10 with Dell Vostro 1200. I not trying to show off my successfull, i just a newbie try to help others but myself still facing problems, maybe Ubuntu guru will help us to resolve the problems that still exists.

Sorry for my bad English.

[SIZE="4"]Vostro 1200 Spec[/SIZE]
- Processor Intel® Core2Duo T7250 (2.0 GHz, FSB 800, Cache 2 MB)
- Chipset Intel 965GM
- Memory 2 GB (2x 1 GB) DDR2 SDRAM PC-5300 
- VGA Intel® Graphics Media Accelerator X3100 256 MB (shared) 
- LAN Marvel 8055
- Wifi Intel PRO/Wireless 3945ABG
- Fingerscan Upek
- Webcam integrated 2.0 mega pixel 
- Hardisk 160Gb
- CDRoom DVD±RW

Dual boot XP and Ubuntu 8.10 with partition :
- 30 Gb Primary NTFS for XP
- 84 Gb Primary Fat32 for data
- 100 Mb Primary ext3 for /boot
- 40 Gb Logical ext3 for /
- 4 Gb Logical for swap


Now Ubuntu 8.10 kernel that i using is 2.6.27-9-generic. Problem that show after upgrade kernel, my wireless cannot automatic detect wireless SSID even the SSID is not hidden. Already install Wifi-radar but still not solve, any solution ?

[SIZE="6"]Software Issue[/SIZE]

- [SIZE="4"]VirtualBox 2.0.6[/SIZE] ([http://www.virtualbox.org/](http://www.virtualbox.org/)) 
This software to make a virtual machine. I use to install XP so i don't have to restart when i want to use Visio. I download the deb file and install success in Ubuntu but after make XP virtual machine i still have problem with USB shares.
Now USB Share problem already solve. Just follow the intruction from uidb4056
[http://ubuntuforums.org/showthread.php?p=6058465#post2](http://ubuntuforums.org/showthread.php?p=6058465#post2)
But remember, not all USB devices is supported by Virtual Box


- [SIZE="4"]GNS3[/SIZE] ([http://www.gns3.net](http://www.gns3.net)) 
Very usefull to simulate Cisco router. I just follow the tutorial book from the website and success.

- [SIZE="4"]Compiz[/SIZE]
I got problem with Compiz, but already solve. After install Compiz from add/remove apllication, i can't setting the compiz. I read the Ubuntu forum and i found if CompizConfig Setting Manager must be install. Just go to add/remove program and find and check Advanced Desktop Effects Settings.


[SIZE="6"]Hardware Issue[/SIZE]

- [SIZE="4"]3G modem[/SIZE] huawei E169 is detected and only have one issue no configuration to switch the mode GPRS or 3G.
- [SIZE="4"]Media button[/SIZE] working without any issue just using rhythmbox music player Except for wireless button.
- [SIZE="4"]Webcam[/SIZE] working only using ekiga softphone
- [SIZE="4"]Fingerscan[/SIZE] must using workaround you can read from here [http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation). The fingerscan now is working but other issues is come with authentication when i want to mount my FAT32 partition, unlock User & group. I decide to not use the fingerscan when login Ubuntu, how ? I just recover my common-auth file.


Regards

Purba

---

