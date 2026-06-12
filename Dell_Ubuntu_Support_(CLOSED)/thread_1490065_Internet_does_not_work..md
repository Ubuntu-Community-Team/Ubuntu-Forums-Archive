---
title: "Internet does not work."
date: 2010-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by schie124 on 2010-05-21
Hey,

I just bought a Dell Studio 15 (only modification being a larger hard drive [http://www.dell.com/us/en/business/notebooks/laptop-studio-1555/pd.aspx?refid=laptop-studio-1555&s=bsd&cs=04&~oid=us~en~4~laptop-studio-1555-anav1~~]("http://www.dell.com/us/en/business/notebooks/laptop-studio-1555/pd.aspx?refid=laptop-studio-1555&s=bsd&cs=04&%7Eoid=us%7Een%7E4%7Elaptop-studio-1555-anav1%7E%7E")) and cannot connect to the internet at all. 

Not wireless. 

Not with a wire.

Nothing. 

I've never used linux before. 

I know the hardware in my computer works because I was on the internet before I erased Windows 7.

Please help!

---

### Post by vdubhack on 2010-05-22
Is your computer even seeing your connections? What does iwconfig or ifconfig give you? What about dmesg?

---

### Post by schie124 on 2010-05-22
Not seeing any connections. I can't even enable my wireless.

iwconfig says
lo     no wireless extensions
eth0 no wireless extensions
wlan0 IEEE 802.11bg ESSID: off/any
mode: managed access point: Not associated  tx-power=20 dBm
Retry long limit: 7    RTS thr:off       Fragment thr:off
Power management: off

ifconfig
Too long to type out manually. I can't copy and paste since I can't get on the internet.

---

### Post by binary10 on 2010-05-22
If you can post the output from 'lspci' and put it on a usb stick for posting,  it might go to help showing up which devices are detected.

---

### Post by schie124 on 2010-05-22
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
  
  00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
  
  00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
  
  00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
  
  00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
  
  00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
  
  00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
  
  00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
  
  00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
  
  00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
  
  00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
  
  00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
  
  00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
  
  00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
  
  00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
  
  00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
  
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
  
  00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
  
  00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
  
  00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
  
  04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  
  08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
  
  09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
  
  09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
  
  09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
  
  09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
  
  09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by ugm6hr on 2010-05-23
Your Netowkring should work. I have the same wifi adapter - and it works fine.

However, you do have to connect by wire first to install the driver correctly:
[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

As for why the wired connection isn't working, we will need more detail.  As before - copy and paste into a text file on USB stick to upload.

Just run all the commands / questions listed in the Wifi help link below - that way you won't have to keep returning repeatedly.

---

