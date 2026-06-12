---
title: "Recognizing Wireless"
date: 2009-11-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Batmanda88 on 2009-11-24
I'm stuck after 4 hours of searching and fiddling. 
I just installed Ubuntu on my Dell today and it's not recognizing the wireless card and i can't find where to enable it. The "Enable Wireless" is checked, but its also saying the device is not ready. I'm using a wired connection right now, and i know my router is fine.
Anyone know a command to enable my wireless and get me connected?
Where do i put in the passkey? WEP? Name of the connection necessary?
Any info would be appreciated :D

---

### Post by Elaztic on 2009-11-24
First of all you should check if you have your Network manager up and running. It resides in your system tray and looks like a bunch of vertical lines or radio kind of icon.
You can also tjek your running applications and look for nm-applet.

It should start at system start up.

If you have the icon but only wired connections are shown your card is most likely not recognized.
You can install the windows driver very easily with ndis-gtk (or is it ndiswrapper-gtk). If it is not on the ubuntu install cd-rom you have to do it by cable.

Search this forum for ndiswrapper....there are some really good guides.

---

### Post by bobcollard on 2009-11-24
> **Batmanda88 said:**
> I'm stuck after 4 hours of searching and fiddling. 
I just installed Ubuntu on my Dell today and it's not recognizing the wireless card and i can't find where to enable it. The "Enable Wireless" is checked, but its also saying the device is not ready. I'm using a wired connection right now, and i know my router is fine.
Anyone know a command to enable my wireless and get me connected?
Where do i put in the passkey? WEP? Name of the connection necessary?
Any info would be appreciated :D
Dell uses Broadcom wireless cards in many computers.  First check your Hardware drivers under System Menu.  It may already be in there, just not installed.  If so there will be two of them.  Highlight one and you need a network connection such as ethernet to download it. If none are shown you can install them by opening Terminal and typing:
    *sudo apt-get install b43-fwcutter*

---

### Post by snowpine on 2009-11-24
> **Batmanda88 said:**
> I'm stuck after 4 hours of searching and fiddling. 
I just installed Ubuntu on my Dell today and it's not recognizing the wireless card and i can't find where to enable it. The "Enable Wireless" is checked, but its also saying the device is not ready. I'm using a wired connection right now, and i know my router is fine.
Anyone know a command to enable my wireless and get me connected?
Where do i put in the passkey? WEP? Name of the connection necessary?
Any info would be appreciated :D

Please let us know which model of Dell you're using. They do not all use the same network card, therefore we are just guessing at how to help you. :)

---

### Post by ugm6hr on 2009-11-24
See the Wifi help link below - it explains how to ask for assistance here.

It is impossible to help without more detail...

---

### Post by squirrelpie on 2009-11-24
Am also having prob finding drivers/activating my internal Dell wireless card. Plugged in a USB Trendnet G Nic which was recognized immediately and am now using on this forum, but would really like to use internal N wireless card. Appreciate help
Specs Dell Vostro 1500, dual boot w XP Pro
jack@Jack-Vostro:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
jack@Jack-Vostro:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jack@Jack-Vostro:~$ lshw -class network^C
jack@Jack-Vostro:~$

---

### Post by teward on 2009-11-24
> **squirrelpie said:**
> 
Specs Dell Vostro 1500, dual boot w XP Pro
jack@Jack-Vostro:~$ lspci
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)


These are your network cards, squirrelpie.  The ethernet controller is used if you connect a wire to get to the internet.  The other Network controller is your wireless.  I removed all the stuff you posted that wasn't needed.  Have you tried a google to find the Linux drivers for these listed cards?

To the original poster of this thread, go into your terminal and type lspci and post its results here.  That will list the devices, and I'll look through and identify what networking cards you have.h

---

### Post by bobcollard on 2009-11-24
> **TrekCaptainUSA said:**
> These are your network cards, squirrelpie.  The ethernet controller is used if you connect a wire to get to the internet.  The other Network controller is your wireless.  I removed all the stuff you posted that wasn't needed.  Have you tried a google to find the Linux drivers for these listed cards?

To the original poster of this thread, go into your terminal and type lspci and post its results here.  That will list the devices, and I'll look through and identify what networking cards you have.h

TrekCaptain, my solution a few posts back will do what he needs for Broadcom.  It includes one that says for BCM43xx, the other has a list of Broadcom and I found mine in there: 
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
Hope this helps him.  It was to use terminal to install the drivers from Dell as follows:
                                 *sudo apt-get install b43-fwcutter*

---

### Post by squirrelpie on 2009-11-25
Thanks for the help. Found solution in Hardware drivers. Activated, downloaded with USB wireless, installed and all internal wireless works after removing USB NIC. Thanks for the help:D

---

