---
title: "Multiple issues with new ubuntu"
date: 2012-02-24
forum: Desktop Environments
---

### Post by gillian.bennett on 2012-02-24
Hi, I recently installed the new version of ubuntu. I have been using ubuntu for about 2 yrs, linux for about 15yrs.  Have to say I have had no end of problems with the installation and now with the system. 

1. Installation - purchased cd from local country - would not boot
2. downloaded server install iso, burned to dvd and commenced installation. Went well until software selection, then kept failing. Ended up de-selecting just bout everything to get it to get past this point.
3. Following installation, found that my boot partition had not been made bootable, and had to re-do installation making sure that the boot flag was set on the boot partition.
4. in desperation tried the desktop install iso, but it couldn't get past the initial startup as I kept getting a muddled multicoloured corrupted display.
5. back to server installation, and persisted with this to get past the software failures and partition was done manually to ensure it was done properly.
6. following successful installation(this actually took about 1 wk as I gave up on ubuntu for a few days to try out gentoo), it actually booted into text mode - yay. Installed gnome, xorg etc and got up a pretty graphic display. Trouble is, can't actually use it, as when an app is opened, the window opens black. Tried a few different things to know avail. 
7 Ended up having to set display to gnome classic to get any apps to actually display in their window.
8. Cant add printers - detects the printer, but will not add it. Have downloaded and installed [FONT=Arial][SIZE=2]foo2hiperc without issue, but the graphic printer adding tool will not add it to my system.

What have I done/missed during this whole frustrating process to get my system working the way it should.  I have a dell desktop amb64 about 4 yrs old, and an benq 24" HD monitor. Hardware and not been an issue on previous versions of ubuntu.
[/SIZE][/FONT]

---

### Post by 23dornot23d on 2012-02-24
Difficult one .... 


Could be that the CDs / Dvds you used were faulty ....

But the fact it happened a couple of times with different discs would lead me first to
think that there may be a problem occuring with the CD reading device ....

If its not and the CD drive is relatively new and in good working condition ... then

the next thing I would look at is the Graphics card and compatibility .... lots of people
had problems with odd screen displays .... often with ATI graphics cards ...


Do this in a terminal and post back the results please
[B]
lspci[/B]

hopefully it will give us some more information to work on.

as an example of what the command gives back here is mine

> 
keith@keith-Aspire-7730ZG:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
keith@keith-Aspire-7730ZG:~$ 



---

### Post by azmyth on 2012-02-24
Check your iso to make sure it is not corrupt. You can do this by comparing the checksum.

[http://ubuntuforums.org/showthread.php?p=11715099#post11715099](http://ubuntuforums.org/showthread.php?p=11715099#post11715099)

If this looks good, when you burn the CD burn it at the _slowest_ setting possible and then when you boot from the CD you can check that CD is good by running the utility that is shown in one of the choices. I got a bad burn before and it displayed the same behavior.

---

### Post by randywilharm on 2012-02-25
If all else fails, do yourself a favor and revert back to version 10.10 (Maverick).
I too thought that Ubuntu improved with each new release but this is NOT the case!
I have had more trouble with 11.10 that any other version of Ubuntu and I just
"down"graded back to Maverick, with good results.

---

