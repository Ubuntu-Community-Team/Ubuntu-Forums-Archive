---
title: "Dell Latitude D630 support for internal Dell wireless 360 bluetooth module"
date: 2007-10-10
forum: Dell  Ubuntu Support
---

### Post by jayant on 2007-10-10
Hello,

I have a _Dell D630_ on which I have been running _Ubuntu Feisty_ for a while now. And now I have almost everything working except for wireless and bluetooth, both these devices work under Windows Vista installed on a different partition. I have a_ Dell Wireless 1505 Draft 802.11n WLAN mini-card_ and after searching on the internet I think that this card may not be functional under Linux. However some people claim to be able to use the_ Dell Wireless 360 Bluetooth module_. And I am interested in trying to make it work for me.

So here is the output of some commands that may be useful.
```
~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0b97:7772 O2 Micro, Inc. 
Bus 005 Device 002: ID 0b97:7761 O2 Micro, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:8141 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000
``````

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)
``````
biswas@abcd:~$ hcitool scan
Device is not available: No such device
biswas@abcd:~$ hcitool dev
Devices:
biswas@abcd:~$
```i have tried the last 2 commands by adding sudo before it and i get the same result.

Any help is greatly appreciated!

Thank you

---

### Post by ijn on 2007-10-11
im on dell inspiron 6400/1505. I had maneged to work my dell wireless wlan draft 802.11n. there is only one way you can do it, for now.the answer is ndiswrapper (try the leteast version 1.48 from sourceforge website) and dell windows driver that you can get from dell suport web site. dell driver is for both 32/64 bit cpu, so just download it. you'r gonna need a good how to to make it but suppose u can find something in ubuntu forums or check lunchpad website.
 my bluetooth has never worked though, but im not intrested on make it work.
good luck

---

### Post by jayant on 2007-10-11
> **ijn said:**
> im on dell inspiron 6400/1505. I had maneged to work my dell wireless wlan draft 802.11n. there is only one way you can do it, for now.the answer is ndiswrapper (try the leteast version 1.48 from sourceforge website) and dell windows driver that you can get from dell suport web site. dell driver is for both 32/64 bit cpu, so just download it. you'r gonna need a good how to to make it but suppose u can find something in ubuntu forums or check lunchpad website.
 my bluetooth has never worked though, but im not intrested on make it work.
good luck

thank you for your suggestion. i downloaded the latest ndiswrapper ( 1.48 ) from sf.net and was able to get my wireless to work. your suggestion and the documentation on the ndiswrapper website were enough to get me through =) . The only problem I had was that I disabled usb support when I first installed it. But it works fine now if i leave usb enabled.

So if someone has still suggestions about getting my bluetooth to work I would be glad to hear.

btw here is the output of my dmesg
```
biswas@abcd:~$ dmesg | tail -f
[   49.408000] Bluetooth: Core ver 2.11
[   49.408000] NET: Registered protocol family 31
[   49.408000] Bluetooth: HCI device and connection manager initialized
[   49.408000] Bluetooth: HCI socket layer initialized
[   49.432000] Bluetooth: L2CAP ver 2.8
[   49.432000] Bluetooth: L2CAP socket layer initialized
[   49.476000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   49.804000] Bluetooth: RFCOMM socket layer initialized
[   49.804000] Bluetooth: RFCOMM TTY layer initialized
[   49.804000] Bluetooth: RFCOMM ver 1.8
```

---

### Post by roblloyd on 2007-12-27
Hi Jayant,

I'm in the same position as you i think, bluetooth just wont work. I've found that the problem arises when you have installed Ubuntu after removing Vista (which the dell d630 is usually shipped with). It turns out that Vista actually upgrades the firmware on the bluetooth module in your machine. One was to fix this is to do an install of XP and manually rollback the drivers and firmware for the bluetooth module and then install ubuntu again..... hmmm not the ideal solution.

I'm still searching for a way to do this from linux, but alternatively im thinking that it may be possible to do all this driver giggerypokery by booting into xp from a usb drive.

If anyone has any thoughts on how to change the firmware on the bluetooth module from Ubuntu, your ideas would be very much appreciated!

Just as a point of reference, This is where i got my information:
[http://onemansjourneyintolinux.blogspot.com/2007_10_01_archive.html]("http://onemansjourneyintolinux.blogspot.com/2007_10_01_archive.html")

---

### Post by WooLLsterQ on 2007-12-28
To roblloyd, I have had the exact same problem but have just managed to sort it. First i downloaded and installed the Dell bluetooth drivers for D620/630 vista drivers, then i went into device manager and scanned for new hardware and it picked it up straight away and is working perfectly. This had been sending me crazy for months.

---

### Post by blidmen on 2007-12-29
Did you make driver installation under Vista or Linux?
In my D630 the blue led is on but bluetooth is not discovered, using a Belkin USB bluetooth adapter it is immediately recognised and working.
Thanks

---

### Post by adrian.oneclick on 2007-12-31
anyone found a solution for the bluetooth to function on a D630?

can't get it to work, pls help d'newbie? :(

---

### Post by blidmen on 2008-01-04
Bluetooth works!
As already explained in another post, you should start using Windows, then connect to Dell site, download the upgrading for Dell wireless 360 bluetooth module, then install it under Windows.
Once in Ubuntu, your Bluetooth works!
BG

---

### Post by evert.kronemeijer on 2008-01-07
Thanks! In the same way, I was able to get my Dell D830 bluetooth module (Vista preinstalled) to work in ubuntu by downloading and installing the updated Vista driver from the Dell support site. This problem had me frustrated for weeks.... :-)

---

### Post by parmdeep on 2008-02-23
for clarification for the bluetooth to work on a D630 with pre installed vista one needs to install the drivers inside vista then insgtall ubuntu and it should work, what about somebody  like myself that had xp preinstalled and then installed ubuntu?(Im not dual booting and have no interest in installing windows again)

---

### Post by nan-tze on 2008-02-24
I'm in the same position as you, Parmdeep. Surely there's a way of getting the drivers without reinstalling windows (at a cost?) then reinstalling ubuntu??

Someone who knows, please help.

---

