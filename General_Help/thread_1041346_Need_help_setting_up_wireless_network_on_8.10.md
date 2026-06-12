---
title: "Need help setting up wireless network on 8.10"
date: 2009-01-16
forum: General Help
---

### Post by iForum on 2009-01-16
Ok so here is my situation

I just dual booted my computer to run vista and ubuntu and i am having trouble connecting my ubuntu to my wireless network i have a Linksys WRT54G router and im using a Gateway M-6750 laptop if someone could please give step by step instructions on how to set it up it would be greatly appreciated

---

### Post by avtolle on 2009-01-16
First bit of information that will be needed: what wireless card or dongle are you using? If a card, go to terminal (Applications>Accessories>Terminal) and run ```
lspci
``` and paste the output here. If a dongle, from terminal run```
lsusb
```and again, post the output of the command here.

BTW, which version of Ubuntu did you install?

---

### Post by iForum on 2009-01-16
I am running Ubuntu 8.10

Here is what happened when i typed in lspci

aner@aner-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03) 
1.	06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

---

### Post by avtolle on 2009-01-16
Just did a Forum search on your laptop; it seems the wireless issue has been very problematic for several, and I don't know that I found any thread where it was resolved. From what I could ascertain, the best potential solution involved installing the Windows 98 driver using ndiswrapper, but that was unclear. I'll poke around a bit more, and if I find something useful, will post back. Hopefully, someone with more knowledge of this problem will see this, and post something useful.

---

### Post by avtolle on 2009-01-16
I must be losing it. See [http://ubuntuforums.org/showthread.php?t=979112](http://ubuntuforums.org/showthread.php?t=979112) and the thread linked in the first post for a potential solution. Good luck.

---

### Post by iForum on 2009-01-16
Thank you so much

---

