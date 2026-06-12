---
title: "how do i make the internal card reader work?"
date: 2009-02-25
forum: General Help
---

### Post by Mzwo on 2009-02-25
hi,

i'm running hardy on a toshiba satellite 200-29l with a built in 5-1 card reader. i just tried using it for the first time, but no luck. when the card is inserted, the relevant light comes up breifly and then goes off again. i can't find a "removably media" entry in places or anyhwere else.

lsusb yields:

```
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

i believe the second entry to be the card reader, since no other usb devices are in use.

lspci gives me:


```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

the card reader seems to be recognised.

what to do? 

cheers,
Mzwo

---

### Post by fragos on 2009-02-25
Card readers that are USB connected should work with no problem as long as the support the card you're trying to read. For example SDHC cards wont work in an older reader for SD cards. It's not unusual for laptops to have a proprietary hardware interface to card readers that would require a special Linux driver. On the desktop USB would always be used for readers. There are inexpensive USB card readers -- those will work even when the built in one didn't. Don't forget to get a reader speced for SDHC as it also works with SD.

---

### Post by heindsight on 2009-02-25
> **Mzwo said:**
> 
lsusb yields:

```

Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

i believe the second entry to be the card reader, since no other usb devices are in use.


A quick google seems to indicate that that usb device is a webcam, does your laptop have a builtin webcam?

> **Mzwo said:**
> 
lspci gives me:

```
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```


Looks like that is your card reader there.

Try running (in a terminal)```
tail -f /var/log/syslog
```
then insert a card into the reader and see if it produces any output (and post it here). That may give an indication of what's going wrong.

---

### Post by CrucifiedEgo on 2009-02-25
I have this same card reader in my Sony VGN-NR260EW.  It doesn't generally work in ubuntu.  There's a driver that was in development for the SD slot, but the MS slot is a lost cause from what I understand.

---

### Post by Mzwo on 2009-02-26
@heindsight: of course, the webcam - yep, got that. just never use it, so completely forgot about it. 

will do the tail-thing as soon as i'm back home. 

Mzwo

PS: i can live with the card reader not working, if i get this to run: [http://ubuntuforums.org/showthread.php?t=1080518]("http://ubuntuforums.org/showthread.php?t=1080518"). any suggestions?

---

### Post by eldragon on 2009-02-26
im really interested in the outcomes of this thread...

ive got a card reader that uses the SDHCI module. but only SD cards work, i cant get sony memory stick cards to work on it :(. never could, already gave up.

are you inserting a SD card or a MS?

what are the outputs of
```

$ lsmod |grep sdhci

```

---

### Post by Mzwo on 2009-02-26
it's an sd card ... output with, or without card inserted?

---

### Post by eldragon on 2009-02-26
> **Mzwo said:**
> it's an sd card ... output with, or without card inserted?

shouldnt matter.

---

