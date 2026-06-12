---
title: "Vostro 1000 no longer shows Wireless card after update"
date: 2008-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by malicestar on 2008-07-05
Hey Guys,

I'm a real newb, and trying to make things work.

I've got a Dell Vostro 1000 running Hardy.  I've been through some trials and tribulations, but always found this forum helpful when in a crunch.  This is the first time I'm not able to resolve my own problem.

After performing a recent update, my Wireless stopped working.  When I say stopped working, I don't mean it won't connect.  It's not there. It doesn't show up from the network dialog box, and under Hardware drivers the 'wl' driver is enabled but not in use.

I did lspci, and got the following output:

gordon@Frenchy:~$ lspci
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
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

Correct me if I'm wrong, but there's no Wireless card there.  Does anyone know what might have happened, and how to fix it?

I appreciate any input, but please use layman's terms, as I"m not that bright.

---

### Post by Hoaxe on 2008-07-07
i'm bumping this because i have a vostro 1500 and have the same problem. wireless was working yesterday, i downloaded an updated and shut off my laptop.

this morning i turn it on, and now it doesn't see my wireless. i wish i could undo the update...

---

### Post by Hoaxe on 2008-07-07
i am posting my log of installed software from last night, this is:

07/07/08/ 04:26
```

Commit Log for Mon Jul  7 04:26:56 2008


Upgraded the following packages:
gstreamer0.10-plugins-ugly (0.10.7-3) to 0.10.7-3ubuntu1
language-support-writing-en (1:8.04+20080410) to 1:8.04+20080630
libblas3gf (1.2-1.3ubuntu3) to 1.2-1.3ubuntu4
libcairo2 (1.6.0-0ubuntu1) to 1.6.0-0ubuntu2
libpurple0 (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.42) to 2.6.24.13-19.44
linux-restricted-modules-common (2.6.24.13-19.42) to 2.6.24.13-19.44
nvidia-glx-new (169.12+2.6.24.13-19.42) to 169.12+2.6.24.13-19.44
openoffice.org-base-core (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-calc (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-common (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-core (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-draw (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-gnome (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-gtk (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-help-en-gb (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-help-en-us (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-impress (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-common (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-en-gb (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-en-za (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-style-human (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-writer (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
pidgin (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
pidgin-data (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
python-uno (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
tomboy (0.10.1-1) to 0.10.2-0ubuntu1
ttf-opensymbol (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
x11-common (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xbase-clients (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xlibmesa-gl-dev (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xorg (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-input-all (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-video-all (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-video-amd (2.8.0-7) to 2.9.0-1ubuntu2.4
xserver-xorg-video-geode (2.8.0-7) to 2.9.0-1ubuntu2.4
xserver-xorg-video-nsc (1:2.8.3-2) to 1:2.8.3-2ubuntu0.1
xutils (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2

Installed the following packages:
openoffice.org-hyphenation-en-us (2.3.1-2ubuntu1)

```

if someone could tell me which one of these affects the wireless, i will roll it back to the previous iteration.

---

### Post by timcredible on 2008-07-07
did you have to run ndiswrapper (system->administration->windows wireless drivers) to get wireless to work first time?  i did to get wireless working on my vostro 1000.  if so, run it again.  it adds the windows wireless driver to the kernel, and if you installed a new kernel, then that driver isn't in that new kernel until you run ndiswrapper again.  you can test this by picking the old kernel at the grub boot screen and see if wireless works again.

fwiw, i never do any updates unless it's a specific app i want a newer version of.  i've been 'not updating' for 8 years now, but i do install a fresh install of linux at least once a year.

---

### Post by Hoaxe on 2008-07-07
hmm, I never had to go through ndswrapper nor did i have the windows wireless option. so i checked my restricted drivers and right below the nvidia driver i see a new device called "wl". i never saw it before. when i try to enable it, i have to reboot the computer and it still isn;t enabled. 
very weird

anyways, i just downloaded the ndswrapper and am now looking for the wireless driver ini file to install it and hopefully get going.

thanks.

---

### Post by Hoaxe on 2008-07-07
no dice,

i got the driver inf file out of the exe file from the dell site. i loaded the inf file into the windows wireless driver option.

this is balls, i didn't need this ndiswrapper before,and i shouldn't now. i'm going to try some other solutions.


edit: aahh!! i can't even roll back to: linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.42

the .42 version isn't there to roll back too! qq

---

### Post by maphdelic on 2008-07-08
I have the same problem.

See dmesg feedback:

```

$ dmeseg
...
[  307.217248] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  307.217267] b43-phy0: Controller RESET (DMA error) ...
[  307.219129] b43-phy0 debug: Wireless interface stopped
[  307.219405] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 7/64
[  307.219487] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  307.225227] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  307.233247] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  307.241202] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  307.249203] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 14/128
[  307.257202] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[  307.368583] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  137.445097] b43-phy0 debug: Chip initialized
[  137.445327] b43-phy0 debug: 32-bit DMA initialized
[  137.465355] Registered led device: b43-phy0:tx
[  137.465378] Registered led device: b43-phy0:rx
[  137.465396] Registered led device: b43-phy0:radio
[  137.465426] b43-phy0 debug: Wireless interface started
[  137.465429] b43-phy0: Controller restarted
[  314.552213] wlan0: No ProbeResp from current AP 00:1e:e5:5d:df:a0 - assume out of range

```

Some suggestion?

---

