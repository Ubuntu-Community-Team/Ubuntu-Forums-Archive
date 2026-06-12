---
title: "White stream of pixels on screen"
date: 2009-08-05
forum: Desktop Environments
---

### Post by Karlossantos on 2009-08-05
Ever since the installation screen of Ubuntu my laptop (new as of yesterday) has had a thin white column of pixels slightly off to the right of the middle of the screen and another on the far left. I also have Windows Vista installed (not my fault), and the problem is not present when I boot that. The problem is not impeding the performance or function of my computer, but it's annoying.

---

### Post by Karlossantos on 2009-08-08
I know you're all probably the 'strong silent type', but a little help would be great right about now. I'm using a HP Pavillion DV7.

---

### Post by Bearded-flower on 2009-08-08
Can you post a screenshot?

---

### Post by Karlossantos on 2009-08-08
It seems the dots are phantoms; they don't appear when your trying to take a screenshot of them. I will try to simulate the effect. Keep in mind that these dots are constantly skittering up and down their little column.

[IMG]http://i156.photobucket.com/albums/t4/karlossantos/Screenshot.png[/IMG]

---

### Post by garikaib on 2009-08-08
Beats me! Are you sure it is not the wallpaper? Try changing it. And even if you are sure it's not the wallpaper try using a light coloured wallpaper. Since the stream is but near invisible over the task bar which has light colours. I think the change will do the trick.

---

### Post by bobince on 2009-08-08
Sounds like it could be a graphics card output problem&#8201;—&#8201;I had something similar on Windows when my old card developed a hardware fault.

What driver are you using (it's  nVidia integrated graphics, right)? Does changing the driver, resolution or refresh rate make a difference?

---

### Post by Vakman on 2009-08-08
> **Karlossantos said:**
> I know you're all probably the 'strong silent type', but a little help would be great right about now. I'm using a HP Pavillion DV7.
:lolflag: That was quite funny :P

Let's verify that the drivers are installed correctly. Please post the output of
```
glxinfo | grep direct
```
Also, so we can see what card you have and other hardware also post the output of
```
lspci
```

---

### Post by Karlossantos on 2009-08-09
glxinfo | grep direct:
[FONT=Courier New]unknown chip id 0x9612, can't guess.
direct rendering: Yes[/FONT]

lspci:
[FONT=Courier New]00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/FONT]

---

### Post by Vakman on 2009-08-09
[QUOTE=Karlossantos;7756254]glxinfo | grep direct:
[FONT=Courier New]unknown chip id 0x9612, can't guess.
direct rendering: Yes[/FONT]

Unknown chip. Though the answer Yes is good :P
All right so, we should reinstall the driver for your Radeon 3200.
Follow [this]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually") to install the drivers. Download them from [here]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and just choose what you have. Let us know if you get it working or need any more help with it. Also what method did you use to install the drivers originally.

---

### Post by Karlossantos on 2009-08-09
Huzzah! Success! The driver installation worked. Thanks Thisislaw and everyone else who took the time to help.

---

### Post by Vakman on 2009-08-09
> **Karlossantos said:**
> Huzzah! Success! The driver installation worked. Thanks Thisislaw and everyone else who took the time to help.

So no more white pixels I assume? And no problem. glad it worked.

---

