---
title: "blender not working"
date: 2012-05-26
forum: Desktop Environments
---

### Post by mandza on 2012-05-26
hi,
i use ubuntu 12.04 and i downloaded blender-2.63-linux-glibc27-x86_64 but it wouldnt work. i dont know why.
is there any additional program i need to download or settings to make?
thanks a lot.

---

### Post by MG&amp;TL on 2012-05-26
...how would we know?

Can you try running it from the terminal (post back if you need instructions) and give us the output?

---

### Post by mandza on 2012-05-26
when i write "blender" in my terminal it outputs this:
if i am running program wrong please help me.

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  32
  Current serial number in output stream:  32

---

### Post by MG&amp;TL on 2012-05-26
Bug. Not anything you can do about it, so I suggest you report it, then get another one (there seems to be umpteen versions of blender). Just to check, how did you install this?

If you want reliability, I can't recommend enough using the repos version.

---

### Post by mandza on 2012-05-26
i had download it form blender.org it was working on 11.10 but now on 12.04 it dont.

---

### Post by MG&amp;TL on 2012-05-26
Ahah, okay. What hardware are you on? Some googling provides some things about flgrx...

---

### Post by mandza on 2012-05-26
i use HP G62 laptop i3 3gb ram

---

### Post by MG&amp;TL on 2012-05-26
That doesn't have an ATI card...can you post what happens if you run:

```
glxgears
```

You might need to:

```
sudo apt-get install mesa-utils
```

Apparently, could be a hardware thing.

---

### Post by mandza on 2012-05-26
i have same output as for blender:


X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by MG&amp;TL on 2012-05-26
Okay...3D problem then.

Can you see if there's any drivers listed under "Additional Drivers", then post:

```
lspci
```

---

### Post by mandza on 2012-06-30
This is output:


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

---

### Post by mandza on 2012-06-30
i dont know how but my blender works now.
not one that i had downloaded but old one that i had used on 11.10, i didnt deleted old files. when i run it from command promt it is working.
Thank you all a lot.

---

