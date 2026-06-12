---
title: "Screen resolution showing 1152x864 instead of 1280x1024"
date: 2009-05-22
forum: Desktop Environments
---

### Post by dbansal on 2009-05-22
Hello All,

A bit new to ubuntu, I'm doing my second install!!

Anyways, on this PC, my screen resolution is all messed up. Instead of showing the correct 1280x1024 im getting only 1152x864 lspci gives me this:

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
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)

Thanks in advance!

---

### Post by dbansal on 2009-05-22
Also got this from compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2562 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards.

---

### Post by aussieboy on 2009-05-22
Check that your xorg.conf file in the "Monitor" section has the modeline command that specifies 1280x1024 and in the "Screen" section the Virtual command is set to 1280x1024.

Most problems occur in this area - especially if the rest of the screen resolutions are OK.


Good luck.

---

### Post by dbansal on 2009-05-22
this is what my xorg.conf file looks like:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by dbansal on 2009-05-22
what should i change it to?

---

### Post by dbansal on 2009-05-23
bump

---

### Post by dbansal on 2009-05-24
bump

---

### Post by dbansal1 on 2009-05-25
you guys are being pooheads!

---

