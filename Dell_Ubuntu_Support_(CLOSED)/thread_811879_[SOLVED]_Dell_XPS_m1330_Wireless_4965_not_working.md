---
title: "[SOLVED] Dell XPS m1330 Wireless 4965 not working"
date: 2008-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dyohanan on 2008-05-29
Hi there, first I need to say that i am a newbie in the Linux Word.
Well my problem is that I tried many flavors of Linux (Fedora 9, SuSe 10.3, Linux Mint) and now Ubuntu 8.04, all of them in 16 and 64 bits version and none of them can connect with the wireless card.

My computer is a Dell XPS m1330, Intel Core 2 Duo T7500 2.2 Mhz., 4 Gb RAM, Nvidia GE Force 8400M amd 200 Gb HD. The wireless card is an INTEL 4965 Wireless N-MINICARD and my Access Point is a 2WIRE HomePortal 1800 HW.

I did an /sbin/lspci and the result is this:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

The only difference between Ubuntu, SuSe and Fedora is that Fedora COULD turn on the wireless card but when I tried to connect the result in the three of them is the Access Point resets.

I already tried with ndiswrapper last version and windows XP drivers and the result is the same, the acces point resets

I visited a lot of forums and did a lot of things but the result is always the same.

So I am begging for helllllp  :frown:

---

### Post by Immolatus on 2008-05-29
OK, go to the dell sight and download the latest drivers for your card (yes the windows drivers). Make a folder in your home folder that's called windows crap or something real obvious like that (you'll have to search for it later) Open up Synaptic: System--->Administration-->Synaptic package manager. Search for ndiswrapper. install all three things that come up. Restart your machine. go to System-->Administration-->windows wireless drivers(at the bottom of the list. Click install new driver and choose it from where we put it before (/home/whateveryournameis/windowscrap/nameofthedriver).

Restart the machine again. If this doesn't work, post back, there are some things we need to adjust K?

---

### Post by John.Gaythorpe on 2008-05-29
My M1330 came with Ubuntu installed (7) and I upgraded it to 8.04 and the Wireless works like a champ!

In fact it works and connects better than my Latitude with the broadcom chip under VISTA! I am posting this now using secure wireless...

John.

---

### Post by dyohanan on 2008-05-29
Immolatus, thank you for your help...

I did what you told me but the result is the same, the access point resets again.

Do you have any more ideas? :)

---

### Post by Rumo on 2008-05-29
Some wireless cards have problems with certain access-points (or vice-versa). Did you check if your wireless works in a different wifi network?

---

### Post by Kernel Sanders on 2008-05-29
I too have a Dell XPS M1330, and I totally failed at getting the wireless card working.

I tried OpenSuse and it worked like a charm. I believe the problem lies with the latest Intel Wireless drivers that are included with Ubuntu.

If a solution can be found, I hope it gets made a sticky!

---

### Post by dyohanan on 2008-05-29
> **Rumo said:**
> Some wireless cards have problems with certain access-points (or vice-versa). Did you check if your wireless works in a different wifi network?
No, the truth is that I did not try with other access point but is a good sugestion and I am going to try it.

---

### Post by dyohanan on 2008-05-29
> **Kernel Sanders said:**
> I too have a Dell XPS M1330, and I totally failed at getting the wireless card working.

I tried OpenSuse and it worked like a charm. I believe the problem lies with the latest Intel Wireless drivers that are included with Ubuntu.

If a solution can be found, I hope it gets made a sticky!
What version do you installed because I tried with 10.3 64 bits and did not work at all.

---

### Post by John.Gaythorpe on 2008-05-30
Okay from my messages file:

May 30 08:07:57 potter kernel: [   25.534976] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 30 08:07:57 potter kernel: [   25.534979] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 30 08:07:57 potter kernel: [   25.643910] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
May 30 08:07:57 potter kernel: [   25.643922] ricoh-mmc: Controller is now disabled.
May 30 08:07:57 potter kernel: [   25.644298] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
May 30 08:07:57 potter kernel: [   25.644336] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection

This is in modprobe.d in /etc:

ipw3945 file:

install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; \
        /sbin/ipw3945d-$(uname -r) --quiet
remove  ipw3945 /sbin/ipw3945d-$(uname -r) --kill ; \
        /sbin/modprobe -r --ignore-remove ipw3945

In /sbin:

-rwxr-xr-x 1 root root 68152 2007-10-15 07:42 ipw3945d-2.6.22-14-generic


So 8.04 came with it...

---

### Post by Kernel Sanders on 2008-05-30
> **dyohanan said:**
> What version do you installed because I tried with 10.3 64 bits and did not work at all.

I tried the 32 bit version. Worked straight out of the box :)

---

### Post by John.Gaythorpe on 2008-05-30
Of course if the software is there is the little switch on the right side switched on?

Dumb question of course.

Some of the other forums have you run: iwconfig

But it is easier if the actual software is there in the first place which it was with 7.xx and 8.04.

John.

---

### Post by dyohanan on 2008-05-30
Hi everyone, first I want to thank each of you. Well this is an update...

I did the following:

In the BIOS I have the option to control wireless, bluetooth and i do not remember what else with an external switch, so I just leave the bluetooth for that switch, so the wireless has to be turn on with software.

Then chatting with a friend he told me to increase the power of transmitting of the access point and I change from 4 to 10. He told me how to do this. 

We did this on windows, so I reboot on linux. i have to do a sudo modprobe iwl4965 and the wireless led turn on and then in a few seconds I am connected to my access point.

So i think all the issue was the access point, but I am going to try with others to be sure.

I almost forgot the wireless card could work with iwl4965 driver or using ndiswrapper and VISTA driver.

So I just want to thank you for all your help and ideas to try to solve this. ):P =D>

---

### Post by elias_vc on 2009-03-22
I had a similar problem and I removed the default network manager by installing a new one, Wicd. Go to [HTML]wicd.sourceforge.net/[/HTML] and follow the instructions. I hope this helps.

Good Luck

---

### Post by rykel on 2010-09-26
Hi, How can you guys label this thread as "solved" when the last solution is to remove Ubuntu Network Manager and install wicd?

This is as good as saying, "Remove Ubuntu, install Fedora and it will work," then identifying the problem as "solved".

Neither is ndiswrapper a good solution because we are back to using a WINDOWS driver on a LINUX computer. Not good.

Anyway, I am also having this wifi-can-see-networks-but-cannot-connect problem with Ubuntu Lucid on a Dell XPS M1330.

---

### Post by sikshady on 2011-03-28
> **rykel said:**
> Hi, How can you guys label this thread as "solved" when the last solution is to remove Ubuntu Network Manager and install wicd?

This is as good as saying, "Remove Ubuntu, install Fedora and it will work," then identifying the problem as "solved".

Neither is ndiswrapper a good solution because we are back to using a WINDOWS driver on a LINUX computer. Not good.

Anyway, I am also having this wifi-can-see-networks-but-cannot-connect problem with Ubuntu Lucid on a Dell XPS M1330.
Hi, did u manage to solve it? 
thanks

---

### Post by praveendvs on 2011-05-17
Hi , I was able to resolve the issue. 
Long story short,I installed Ubuntu 11 on my windows vista as a dual boot. So when I start my machine I get to choose windows vs Ubuntu. So once I entered into Ubuntu my Dell xps was unable to recognize any wireless network even though "Enable Wireless" was checked. I connected my Dell through Ethernet and then did a Hardware driver update (bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3)).
After restarting my Dell detected the wireless network. I just entered my password and it started working. 

Thanks,
Praveen

---

