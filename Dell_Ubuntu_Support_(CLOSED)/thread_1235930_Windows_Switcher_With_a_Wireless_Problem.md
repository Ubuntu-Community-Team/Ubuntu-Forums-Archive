---
title: "Windows Switcher With a Wireless Problem"
date: 2009-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LeftClicker on 2009-08-09
To Whom It May Concern:
   I recently installed Ubuntu 9.04 Desktop on my Dell Inspiron 2200.  The problem is that, while my wireless worked with Windows XP Home Edition, Ubuntu does not see any of the networks that my iPod touch does.  In fact, it sees no networks at all.  I opened the case and reseated the MiniPCI card, as it seemed loose, but to no avail.
   Here is system information taken directly from the System Info screen (press F12 during startup):

System Info
System = Inspiron 2200
BIOS Version = A03
Service Tag = 4S0VJ71
Asset Tag = {none}
Ownership Tag = {none}

Processor Info
Processor Type = Celeron M
Processor ID = 06D8
Processor Clock Speed = 1.40 GHz
Processor Cache Size = 1024 KB
Hyperthreading Capable = No

Memory Info
Memory Installed = 512 MB
Memory Speed = 333 MHz
Memory Channel Mode = Single
Memory Technology =  DDR SDRAM

Device Info
Primary Hard Drive  = 30 GN HDD
Modular Bay Device = CD-RW/DVD Combo
Video Controller = Intel 915GM/910GML Graphics
Video BIOS Version = 1205
Video Memory = 8 MB
Panel Type = 14" XGA
Native Resolution = 1024 by 768
Audio Controller = Sigmatel 9752
Modem Controller = Connexant D110 MDC
MiniPCI Device = Wireless
Bluetooth Device = {none}
AC Adapter Type = 60 W

Thanks in advance,
LeftClicker

---

### Post by matthewbpt on 2009-08-09
to fix your problem we need to know what wireless card you have. Open a terminal screen in Ubuntu (Alt-F2 on the keyboard, type in 'gnome-terminal' and press enter) type the following, press enter and give us the output:

```
lspci
```

this command will list all your pci devices.

---

### Post by LeftClicker on 2009-08-09
Sorry, Ubuntu had a problem copying to my flash drive so I had to type it directly:

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

---

### Post by matthewbpt on 2009-08-09
Looking at your lspci output, it seems you have a Broadcom BCM4318 wireless card. A little googling reveals that Broadcom has not released linux drivers for this wireless card (stupid unfriendly hardware companies!). Fortunately there's still a solution. You will have to use 'ndiswrapper', this is a program for linux which uses the windows wireless driver to make an unsupported wireless card work in Linux, its actually very clever. I found a page with instructions on how to do this [http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/) it says it's for Intrepid but it should work fine with Jaunty too.

---

### Post by LeftClicker on 2009-08-09
Dear matthewbpt,
  I tried the [http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/) instructions but the driver was not the right one.  I looked at

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&&SystemID=INSPIRON%202200&os=WW1&osl=en&servicetag=&catid=-1&impid=-1&deviceid=9304&libid=32&releaseid=R134855&formatcnt=1&vercnt=1](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=19&l=en&s=dhs&&SystemID=INSPIRON%202200&os=WW1&osl=en&servicetag=&catid=-1&impid=-1&deviceid=9304&libid=32&releaseid=R134855&formatcnt=1&vercnt=1)

for Dell Inspiron 2200 drivers in the Network section but there did not seem to be any for my network controller (which I noticed uses 802.11g; I am not sure if my network uses that).  I am not sure what to do at this point, aside from installing a more compatible network card (which I am sure I can afford and correctly connect).  If you could either specify a driver that works without too much complications (I am an OS X guru and have some Windows knowledge, but I know too little about Ubuntu) or a network card that is known to work (well) with Ubuntu 9.04, I could make do.
Thanks for your continued speedy help,
LeftClicker

---

### Post by LeftClicker on 2009-08-10
Dear matthewbpt,
   Thank you for your continued support.  Using a link in the comments of the site you referenced, I was sent to an Ubuntu forum much like this one where someone had linked to another person's guide.  They cited

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

as a source of information that hadn't helped them.  While this source was intended for Feisty and Dapper, I found it worked for me on Jaunty (9.04) after rebooting.  My Internet connection is now fully functioning.  I give you 5/5 for helping me, and I learned a lot in the process.
  Thank you.

I wish you well,
LeftClicker

---

