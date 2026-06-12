---
title: "Tearing with Conky and Cairo"
date: 2014-07-15
forum: Desktop Environments
---

### Post by AnotherKevin on 2014-07-15
Hi All!

I installed Cairo dock (looked and worked GREAT!) and then I installed Conky.  Now that I have the 2 installed and running I have screen tearing.  I went through here and the net for hours trying to find a solution to no avail.  

[I]_System_: HP All-In-One PC-100, AMD Athlon(tm) II X2 250u Processor, 3 GiB RAM, Built in ATI graphics, Kubuntu 14.04 with KDE 4.13.2
Results of lspci:

[/I]```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)



```

Result of glxinfo |grep OpenGL:

```


OpenGL vendor string: X.OrgOpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL core profile version string: 3.1 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 1.40
OpenGL core profile context flags: (none)
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:



```

I have made absolutely NO progress with this issue, except that I changed the update interval in Conky to 3.0,  which at least allows it to look like it's not so obviously tearing.  Nothing helps Cairo to look better.

I tried installing libsdl1.2debian from ppa:timo-jyrinki/ppa,  as suggested in a thread on another site, but there was no change...

Help!  :confused:

Thanks!  

Kevin

---

### Post by Frogs Hair on 2014-07-15
Hello: AnotherKevin 

Changing the window type for Conky might help. There are different options that can be used.(see underlined)

 Example from a .conkyrc: ```
own_window yes
own_window_type panel  # _other options are: override/dock/desktop/panel_
own_window_transparent yes

```

---

### Post by AnotherKevin on 2014-07-15
> **Frogs Hair said:**
> Hello: AnotherKevin 

Changing the window type for Conky might help. There are different options that can be used.(see underlined)

 Example from a .conkyrc: ```
own_window yes
own_window_type panel  # _other options are: override/dock/desktop/panel_
own_window_transparent yes

```

Thanks (**again!**) Frogs Hair.  It didn't help, though...  Still tearing.  I'm assuming that running Conky started the issue, as you seem to be.  Is there a Conky info source that's concise and not too technical that you're aware of?  If I had something clear and not too deep to refer to, I could probably figure it out and post my success (hopefully).

Kevin

---

### Post by AnotherKevin on 2014-07-15
I installed Conky Manager, the UI for configuring Conky.  So, Conky is no longer tearing, but Cairo still is.

I guess I can live with Cairo's tearing, though I would like to be rid of it.  You can only tell it's tearing when I mouse-over the dock.  Otherwise, it looks normal...

Kevin

---

### Post by AnotherKevin on 2014-07-16
I still have screen tearing on Cairo.  Any one else have another idea?

Thanks,

Kevin

---

### Post by Frogs Hair on 2014-07-16
Tearing is usually graphics related. Are you using proprietary graphics drivers or the default open source drivers ?  I have no experience with AMD/ATI graphics on Linux so feel free to bump the thread as needed.

```
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
```

---

### Post by QIII on 2014-07-16
With 14.04 there is no proprietary ATI  driver for pre-HD 5000 series graphics cards.  So installing the proprietary driver is not an option.

Stop conky

```
killall conky
```

and look to see if tearing is still a problem in other applications, such as video.

---

### Post by AnotherKevin on 2014-07-18
Thanks, QIII.

I kinda figured that out.  Last time I buy an all-in-one board of ANY brand...

I deleted Conky and Cairo was still screwed up, so I deleted Cairo, too.  I'm sticking with "native" KDE stuff, now.  Not quite as pretty, but stable and functional...

Thanks again!

Kevin

---

