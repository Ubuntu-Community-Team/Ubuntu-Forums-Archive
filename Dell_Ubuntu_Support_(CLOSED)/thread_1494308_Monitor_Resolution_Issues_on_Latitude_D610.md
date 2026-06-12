---
title: "Monitor Resolution Issues on Latitude D610"
date: 2010-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by woohhaa on 2010-05-26
I have a Dell Latitude D610 and I am running 10.04, installed 25May10. I can not get a resolution higher than 1024x768 on this system. 

I have tried xrandr commands suggested on other threads, which work on my optiplex GX520, but cause the system to go into low graphics mode if I run them on the D610. If I go to system-> monitor it shows the display as unknown and only has the one resolution to choose from. 

Any help would be greatly appreciated.

---

### Post by mikewhatever on 2010-05-27
What are the specs of that laptop? What's the graphics card?
Can you post the output of **lspci** from Applications->Accessories->Terminal.

---

### Post by woohhaa on 2010-05-27
Intel Pentium M 1.60GHz
RAM 1.2GB 

Ubuntu release 10.04 
kernel linux 2.6.32-22-generic 
gnome2.30.0

Lspci Results are as follows:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by mikewhatever on 2010-05-27
According to the output, you have an Intel 915GM/GMS/910GML Express Graphics Controller. I've also looked up 'Dell latitude 610' and it appears to be a 14" screen notebook, about 5-6 years old. What higher resolution do you expect to get on a 14" screen? Even if the GMA900 could do it, I really doubt the screen could.

---

### Post by woohhaa on 2010-05-27
Preferably I'd take anything higher but if it won't do it that is fine. I can work with 1024 x 768 though I'm pretty sure I've seen users with this model running XP at higher resolution. 

Thanks for your help.

---

### Post by woohhaa on 2010-05-27
Here is an interesting link for anyone else having similar issues. 

[http://answers.yahoo.com/question/index?qid=20080702064315AAD6klN](http://answers.yahoo.com/question/index?qid=20080702064315AAD6klN)

---

### Post by 1967tempest on 2010-07-19
I guess that is what I am dealing with.  Not sure if the laptop was used at a higher screen resolution as the windows XP failed.  Slicked it to 10.4...I can live with it...

---

### Post by woohhaa on 2010-07-19
I was never able to get any higher resolution though I did find a D600 I might scavenge the LCD from and see if it is any better.

---

