---
title: "System installed on a External Hard Drive, Themes aren't loading"
date: 2011-05-17
forum: Desktop Environments
---

### Post by GTMoraes on 2011-05-17
Hey. Basically what I've said.
I've installed Ubuntu 11.04 Natty Narwhal on a External HDD (320GB Samsung S2). Worked like a charm. Bit slow to boot up and load programs, but after a while, works great.

I installed it on the external HDD for one purpose: Work anywhere with Ubuntu, no matter which computer I use.
I was thinking that was impossible, but I've tested thru several platforms (3 Notebooks, 2 netbooks, all Intel and one AMD Desktop). All worked flawlessly (32 Bits PAE activated and no matter how many cores are active, just works), BUT the themes.
For no apparent reason, themes works on the computer I've installed Ubuntu on the HDD. It has his own Internal HDD with Windows 7 and two NTFS partitions.

Themes are stuck to the default boring-white from Gnome. I can only change the window controls.

Compiz works, Wireless works, video works, sound works, filesystem works, system works - themes fail. Feels like I've hit my feet's little finger on a chair.


P.S.: Ext. HDD is partitioned like this: 300GB FAT32 (it's my pop's HDD, he wants it this way), 18GB EXT4, 2GB Swap.

some pics attached
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by GTMoraes on 2011-05-17
I've found a workaround

1 - Open Terminal
2 - paste this on the Terminal:
    gksudo gedit /etc/xdg/autostart/gnome-settings-daemon.desktop
3 - Type in the password
4 - Change the 4th line
    Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon)
to exactly this:
    Exec=bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"
5 - Save the file.
6 - Restart

Works like a charm, but undeniably is a workaround. Should have a proper fix.
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

