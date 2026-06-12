---
title: "Yet another noob requesting help :)"
date: 2009-02-07
forum: General Help
---

### Post by jojo490 on 2009-02-07
Hey guys. Long story short, I have no drivers installed, nor do I have the option for any through system -> administration -> hardware drivers.

I've spent hours on Google, and have decided to finally concede and ask you guys for help...


Thanks in advance!

--jojo490

---

### Post by utnubuuser on 2009-02-07
Hi jojo490

What do you need drivers for?  VideoCards? Wireless?

If you post the output of > lspci (from a terminal), and/or > dmesgsomeone will most likely be able to tell you what to look for.

---

### Post by mb_webguy on 2009-02-07
Actually, yes you do have drivers installed.  If you didn't, you wouldn't be able to use your keyboard, monitor, or any other piece of hardware connected to your computer.

What you don't have are any *proprietary* drivers.  That is, drivers provided and maintained by the hardware companies rather than the Linux community.

If your system works, then you don't need any proprietary drivers.  However, some devices -- video cards in particular -- often work better with the proprietary drivers, typically because the hardware manufacturer won't release the specifications to their hardware so that the community can make decent drivers of their own without a lot of reverse engineering.

The Hardware Drivers application should actually be called *Proprietary* Hardware Drivers.  It automatically detects if there are any suggested proprietary drivers available for your system.  If no drivers are listed there, then you probably don't need any.

---

### Post by jojo490 on 2009-02-07
Fast reply...Thanks!
My video card is the 
 Intel Corporation Mobile GM965/GL960

Wifi card is 
 Intel Corporation PRO/Wireless 3945ABG 

What I meant though is the hardware driver tab says I have none, not that I really dont. Also, my video card is blacklisted...:( Does that mean I cannot get the "wobbly windows" effect?

---

### Post by mb_webguy on 2009-02-07
As I said, Hardware Drivers is only concerned with proprietary drivers.  If Hardware Drivers says that there are none available, it means there are no *proprietary* drivers available.  The easiest way to see if you're going to be able to use advanced desktop effects is to try to apply them by going to System->Preferences->Appearance, clicking on the Visual Effects tab, and clicking the Extra radio button.

And Hardware Drivers won't show you anything about your wireless card.  I think you're probably going to need to install the Windows driver using ndisgtk.  Can you run the command "lspci" in the terminal and post the output?

---

### Post by jojo490 on 2009-02-07
Good point utnuubuser...here's my lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
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
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)



After a couple hours of tinkering around and turning the blacklisting off, I did manage to get high effects turned on...very cool looking :)

However, I still cannot render 3D in complex video-games, and I know it isnt WINE. Either way, being new to linux, I'm having a blast :D

---

### Post by mb_webguy on 2009-02-08
Does your wireless card not work?  Because according to [this]("http://intellinuxwireless.org/"), the driver for your card has been integrated into the Linux kernel since version 2.6.24.  What kernel are you using?  If you don't know, open System Monitor and check the System tab.

As for your video card, I've seen several older posts about known issues with that chipset and Compiz, which was why it was blacklisted.  Make sure you have the xserver-xorg-video-intel package installed.  You may also need to make some changes to your xorg.conf file, but I'd have to see it first (after you've made sure you have the xserver-xorg-video-intel package installed, of course).

---

### Post by jojo490 on 2009-02-08
uhh...I'm a TOTAL noob. How would one go about installing this?

I tried opening the terminal and typing 

sudo apt-get install xserver-xorg-video-intel

said it doesnt exist.

my xorg, however, is 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



thanks again guys for the great help :D

---

### Post by jojo490 on 2009-02-08
oh yeah, im online on my laptop now

---

### Post by mb_webguy on 2009-02-08
It said the package didn't exist?  It's in the main repository!  Maybe your package index is broken...  Try the command "sudo update-apt-xapian-index", then "sudo apt-get update", and "sudo apt-get install xserver-xorg-video-intel" again.

Instead of installing it from the terminal, you could try Synaptic instead (though you should still run the update-apt-xapian-index command first).  When you open Synaptic, first go to Settings->Repositories.  On the Ubuntu Software tab, click the "Download from:" box and select "Other".  Click the "Select Best Server" button, and choose the server that it picks for you.  Then close the Software Sources window and return to Synaptic.  You'll be prompted to reload your sources, so click the reload button.  Now search for the package and (assuming you find it, which you really should at this point) install it.

---

### Post by jojo490 on 2009-02-08
How do you guys know these things?! lol

anyways, I did all the steps and they worked. It still doesnt list any drivers in the proprietary driver's list, but all the frills and such are working once again. Thanks again!

--especially mb_webguy

---

### Post by mb_webguy on 2009-02-08
Glad I could be of help.

And we know these things the same way you will -- by doing.  It's an ongoing process.  I answer a lot of threads on this board, but I occasionally ask a few, as well.  And what I know, I know because I've encountered that particular issue or one similar to it.  The more you do, the more you know.

---

