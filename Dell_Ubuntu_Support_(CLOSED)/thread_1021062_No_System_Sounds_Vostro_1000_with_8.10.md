---
title: "No System Sounds Vostro 1000 with 8.10"
date: 2008-12-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Lifes_Reject on 2008-12-24
Hi everyone:  I've got a Vostro 1000 with Intrepid 8.10 installed, Runs "GREAT" except there are no System Sounds....  :confused:

I tried 8.04 LTS and it will boot but the Login In Screen doesn't jive with my Ati Card Screens all scrambled, and the One before that had the same problem with my Ati Card.
So there's No Way to tell you if their sounds worked or not.

I can Play Audio Files got sound, Video also got sound, and Games as well.

Login sounds play that's it...

No Logout sound, minimize, maximize, etc....

I tried Linux Mint 5 sound played fine until they upgraded the sound files.
Linux Mint 6 same problem as this.  I can't find away around this No Matter how many Googles, Forum's Searches I do, or Forum Post that I make....   :sad:

Anyone have any Ideas?  I'm at the end of my Bag of Tricks....
Below is the results of my lspci I don't know if that might help or not?

If it doesn't tell me the other Command Lines you might want me to try and I'll post them here....

rickity@daddysdell:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
rickity@daddysdell:~$ 

Thanks for any Ideas/Advice....    :)

---

### Post by ridgeland on 2009-01-05
I played with my sound files because I could not get the login wav file I wanted to stick.  I ended up converting the wav to ogg and copying in over the original file.

First when you go to 
Menu -> System -> Preferences -> Sound
then to tab "Sounds" then click on the > by the sound do they all play as expected?
Have you changed any sound to play?  If so then theme: Ubuntu has been replaced by theme: Custom.

The file I overwrote was in:
/usr/share/sounds/ubuntu/stereo

---

