---
title: "unable to boot with ATI/NVIDIA graphics cards"
date: 2008-03-07
forum: Dell  Ubuntu Support
---

### Post by ATIuser on 2008-03-07
I switched from the ATI card I was using to this new NVIDIA because I've heard NVIDIA works better with linux. However, I'm still having the same issue I had with the ATI card. That issue being that when I try to boot Linux with my PCI video card, it stops (not going any further) when it tries to load the hardware drivers. So in other words, the only way I can get into Linux is by using the on-board graphics chip-set. I tried both the unified and legacy open source drivers - nothing. Tried using the restricted drivers manager to install proprietary drivers - nothing. Tried using envy to install proprietary drivers - nothing.

The drivers are all installed and I can select which ones to use, it just doesn't want to load the drivers when booting with either the ATI or NVIDIA cards on either Ubuntu Gutsy or Linux Mint Daryna.

In addition to this, when using the restricted drivers manager or envy to install the proprietary graphics drivers, it configured the xorg.conf file to use an NVIDIA driver for the intel chipset, which screwed things up beautifully when trying to boot back in with the on board graphics. Only way in was to boot in recovery mode via onboard graphics - re-edit the xorg.conf file to use the open source intel driver and issue a reboot command. 

One thought however.... when booting with the xorg.conf file created by the installation of the proprietary driver - using the on-board graphics, the last message I see is that CPU frequency scaling is not supported. - could this be the issue? and how do I go about supporting CPU frequency scaling - must I upgrade my BIOS to support that?



Edit: I've tried the VESA and VGA generic drivers as well and they don't seem to want to work. I did some further digging, looking thoroughly at my xorg.conf file and read the man page on it. I figured that having two devices in there might have been messing things up for the nvidia card, so I extracted all the information for the nvidia card and made a separate file for it, identical to the xorg.conf file I am now booted under for just the intel card - obviously the exception to that being the Device section with relevent driver info. It still doesn't want to load any drivers for the card even when it is in a file by itself.

---

### Post by gbrainin on 2008-03-08
I doubt I'll know the answer, but I have some questions:

1. What is your hardware configuration?  Which NVidia card are you using, in what computer?  More experienced users than I will probably find some use if you post the output of the 'lspci' command.

2. Have you tried booting from an appropriate live CD/DVD with only the NVidia card active (*i.e.*, on-board graphics turned off in the BIOS)?  If so, did you get the same error?

3. Why do you have more than one xorg.conf?  Or are you just talking about backup copies made when a program (like envy) modifies the file?

---

### Post by ATIuser on 2008-03-08
1. not booted into Linux at the moment, so I can post that back after a while when I get back from starbucks.

Edit, here is the output of sudo lspci
```

chris@Linux-Mint:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:04.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
01:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
chris@Linux-Mint:~$ 

```

2. yes - that same behaviour was exhibited from even the first time that I tried installing Fedora Core 4, then Ubuntu Feisty, (there was no Linux distro present on my machine at this point.) Then on the suggestion that someone here presented, I switched over to my onboard graphics through BIOS, and the live CD was able to boot. Now I've installed Linux Mint, but it's live CD would not boot through the PCI card either.

3. I have about 20 different variations of xorg.conf that I have tried using, of course each time I make a new one - the old one gets backed up with a name like "xorg.conf.intel" or "xorg.conf.nvidiaproprietary"

---

