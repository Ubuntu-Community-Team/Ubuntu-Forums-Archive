---
title: "no notification for memory card"
date: 2010-08-26
forum: Desktop Environments
---

### Post by carpman on 2010-08-26
Hello, am finding that kde device notifier is not seeing my memory card (sdcard) when plugged into the memory car slot on laptop?

Card see the card with fdisk -l

```
Disk /dev/mmcblk0: 8015 MB, 8015314944 bytes
121 heads, 42 sectors/track, 3080 cylinders
Units = cylinders of 5082 * 512 = 2601984 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

```

```
04:09.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
04:09.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 09)
04:09.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 04)
04:09.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

dmesg show on insert
```
[85185.898649] mmc0: new SDHC card at address b368
[85185.898872] mmcblk0: mmc0:b368 SDC   7.46 GiB 
[85185.899012]  mmcblk0: p1

```

any ideas?

cheers

---

### Post by dabl on 2010-08-26
Although your dmesg doesn't show that it is USB, most SD card readers are actually USB devices.  Can you run ```
lsusb
``` and see it?

Check Rog131's post down this thread -- it's not real recent, but the links may point you toward a solution:  [http://kubuntuforums.net/forums/index.php?topic=3110295.0](http://kubuntuforums.net/forums/index.php?topic=3110295.0)

and also [http://kubuntuforums.net/forums/index.php?topic=3110415.0](http://kubuntuforums.net/forums/index.php?topic=3110415.0)

---

### Post by carpman on 2010-08-26
QUOTE=dabl;9768780]Although your dmesg doesn't show that it is USB, most SD card readers are actually USB devices.  Can you run ```
lsusb
``` and see it?

Check Rog131's post down this thread -- it's not real recent, but the links may point you toward a solution:  [http://kubuntuforums.net/forums/index.php?topic=3110295.0](http://kubuntuforums.net/forums/index.php?topic=3110295.0)

and also [http://kubuntuforums.net/forums/index.php?topic=3110415.0](http://kubuntuforums.net/forums/index.php?topic=3110415.0)[/QUOTE]

Thanks for reply, lsusb


```
susb
Bus 007 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0ac8:c302 Z-Star Microelectronics Corp. Vega USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


USB sticks work fine.

Will check links out.

---

### Post by carpman on 2010-08-26
Hello, ok going to system settings > advanced > removable devices i can see the card appear and disappear when i insert and remove it but it does not get shown in notifier or dolphin even is set to automount on attach?

---

### Post by dabl on 2010-08-26
It sounds like the hardware and underlying OS are working correctly, but something in KDE is not.  Did it ever work correctly, or is this a new installation?

I think the notifier is a KDE 4 widget, isn't it?  (I'm away from my Kubuntu system at the moment).  If you click the "cashew" in the upper right corner of your screen, and "unlock" widgets, and then "Add widgets", it will pop up the list of all widgets.  Scroll down that and see if the device notifier is installed.  If not, install it.  If it is, remove it.  In the latter case, I would restart the X server, or even reboot the system, and then install the device-notifier again.  Don't forget to "Lock widgets" when you are done working with it.

If none of that helps, you might try (with the SD card NOT in the slot) reinstalling plasma-desktop.

---

### Post by carpman on 2010-08-27
Thanks for reply, i tried the remove applet trick and it worked as in now i can see it in the notifier, trouble is there is no way to mount it?

Normally there is indicators to mount or unmount but with this card there is not? If i plugged usb stick in there is!

cheers

---

