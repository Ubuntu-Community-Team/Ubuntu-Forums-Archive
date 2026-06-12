---
title: "Ubuntu 7.10 on Dell 500 laptop"
date: 2008-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Eye3 on 2008-10-14
I have a Dell 500 (Vostro) laptop with factory loaded Ubuntu 7.10 Gutsy Gibbon.

1. The caps lock freezes on startup, at the login screen. xmodmap -e "clear Lock" doesn't work. This problem hasn't gone away even after updating the OS using the Update Manager. But if I logout and login again the caps lock unfreezes.

2. This model (500) is not listed in the wiki under [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04). Which iso should I use to upgrade to Hardy Heron? Can I instead use the ubuntu-8.04.1-alternate-i386.iso from Ubuntu without causing problems?

Thanks.

---

### Post by sLovetz on 2008-12-15
Eye3, I have the same laptop with preinstalled Ubuntu 7.10
Do you succesfully upgrade you Dell 500 to 8.04 or 8.10?
I want to upgrade my laptop, can you, please, tell me how to do this step by step? I read a lot of manns, but afraid to lost some hard possibilities of my laptop in newer version. OEM drivers for hardware will work properly in 8.10, can I lost them in 8.10?
Sorry for bad english.

---

### Post by DieB on 2008-12-15
well, for the hardware issue, there is never a guarantee, but in most cases, newer versions support more hardware and better.

for the laptop, someone on our side, missed to finish his work, but [here]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron500m") is a 8.04 alpha test report.

with the alternate-cd u might always roll right, a wired internetconnetction would be better, but for more see:
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)
section 4 is about the alternate cd.

hope it is a help

---

### Post by DieB on 2008-12-15
for more info on your hardware check lspci inside a terminal (applications-access-terminal or Alt+F2: gnome-terminal).

interesting are graphic and wireless.

---

### Post by sLovetz on 2008-12-16
> **DieB said:**
> for more info on your hardware check lspci...
interesting are graphic and wireless.
Thank you for your help!
This is my lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
 
What do you think?
P.S. I have Dell Vostro 500 cm.540 N828F

---

### Post by DieB on 2008-12-16
well for following line of your printout,

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)

 i found some older forum threads which mention that it doesn't work (but those are about half a year old and a newer bug report on launchpad (that effects 8.10).

i'm sorry i will not tell u "go" cause i don't like to be the person u'd be angry about if it won't work, but if you wish to update and run into problems I#m pretty sure u might find a solution with the help of

[www.uboontu.com](www.uboontu.com)
 (it's a wrap up of google for ubuntu)

but still u got 4 months to think about it until i would definitly do it (due to security updates)

---

### Post by sLovetz on 2008-12-16
Result of lspci command in 8.10(LiveCD) the same as in 7.10, does it means that all my hardware will work fine in 8.10?

---

### Post by DieB on 2008-12-18
not necessseraly, as for lspci it only prints what hardware is attached
and NOT if there is a driver or something. As mentioned above there is no guarantee, even in open source licenses they mostly don't dare to give any kind of guarantee.

I would try the risk if it did run on 7.10 it should also do so with 8.04 - even there had already been 8.04.1 (with lots of fixes).

But it is always wise to stay cautious, i would only try it out, if u got some time and needn't have to do some important work. The comming holidays might be a good idea, due to many are at home and u therefore should get even more help here on the forums.

Pls let all of us know what your expierences are if u dare to update, and probably u got some spare time to complete the work a other has already started. [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron500m](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron500m)

happy holidays ;)

---

### Post by sLovetz on 2008-12-21
> **DieB said:**
> happy holidays ;)
Thanks;-) I burn DVD+R DL with ubuntu-dell-reinstall.iso from my hard disk, try to boot with it - it's OK.
After that I install LinuxMint-6 Main from LiveCD. I can't try Ethernet and Wi-Fi yet coz I have some problem with provider (no free ports for new users like I'am, only in january), all other hardware works fine. I try LinuxMint, coz it have all media codecs "from the box" - this is very important for me now (coz I have no internet connection for downloading them).
Mint is very nice distr, all os grafic effects works with max settings and very quickly. Will try Mint more)

---

