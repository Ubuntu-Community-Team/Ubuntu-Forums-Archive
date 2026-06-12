---
title: "Mounting Flash Card on Networked Printer"
date: 2009-01-01
forum: General Help
---

### Post by krionic on 2009-01-01
OK. So, I have an HP 3210 All-In-One (Printer/Scanner/Copier). I can print to it. I can scan from it. All's well on those fronts. It's connected to a Linksys WRT54g router that's been firmwared to be a wireless bridge (one desktop and the printer are ethernetted to the bridge which connects to my Netgear router). My Linux machine is hooked up directly to said Netgear. Here's the thing:

This particular printer has a port to put camera memory cards in. From Windows, I can (Win)+R and type \\10.0.0.110 and I get a file window right to the card that's loaded in it. For reasons beyond my control (at least, I hope it's not something I've done), I can't load XP (story below). I can't find the correct syntax to mount my memory cards so I can download the pictures.

I've tried:
sudo mount -t vfat 10.0.0.110:/ /mnt/Drv1
sudo mount -t vfat 10.0.0.110/ /mnt/Drv1
sudo mount -t vfat 10.0.0.110 /mnt/Drv1
sudo mount -t vfat @10.0.0.110:/ /mnt/Drv1
other variants with the @ as without
All the above with -t auto

Results every time: 'mount: special device <insert device name used> does not exist.

Remember, I can view from Windows so I don't think my firewalls on both devices are blocking any ports normally needed for this connection.

Couldn't find anything in the forums or on google after a 2.5-hour search (my apologies if I missed something I should've seen). Everything I found has to do with getting two computers talking to each other with CIFS file systems and such. Any help would be greatly appreciated!

I work New Year's day this year, so excuse me if I don't answer right away.

==========================================================================
OK. I seem to be cursed in that every hard drive I run WinXP on seems to fail. After my WD 500GB crashed, I got a Seagate 500GB drive, installed XP, and when my WD replacement came, I installed Ubuntu on it. After some problems with the boot loader going crazy when I added a drive that BIOS automatically connects in an order that puts it prior to my other 3 drives (sdb, sdc, sdd), I wound up wiping the boot loader option and use the ASUS loader to choose which drive to boot. It's set to load the Ubuntu drive as a second option if it can't load Windows. Now the Seagate 500GB drive has an electrical failure (S.M.A.R.T. Self-test execution status: (  89) The previous self-test completed having the electrical element of the test failed).

---

### Post by krionic on 2009-01-02
Thanks to anyone who took the time to read this. I figured it out.

HP printers provide access via a driver - HPLIP. The driver comes pre-loaded in Ubuntu. The flash card is not mountable unless the printer is connected to the computer via usb. For networked printers where a usb connection is not possible (my case they are in two different rooms), you use the hp-unload utility. However, at 12kb/s, this connection was ridiculously slow for me (what usually takes a couple of minutes took a couple of hours). I would recommend anyone having this problem use a card reader, or keep the usb cable handy.

The hp-unload utility is not documented anywhere other than the HPLIP web site, and then it's only referenced in Note 4 on the page detailing supported capabilities. I didn't have a usb cable of the right plug type to connect to my camera. It's probably boxed somewhere, since I never use it. I did find an old card reader while I was digging for the cable, though, so problem solved.

---

