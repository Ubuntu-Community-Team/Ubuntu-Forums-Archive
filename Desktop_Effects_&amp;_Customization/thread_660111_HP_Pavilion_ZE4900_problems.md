---
title: "HP Pavilion ZE4900 problems"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by hyp3rdrv on 2008-01-06
Hey guys, I am a complete noob to Linux but so far I love it - aside from a few issues.

I have an HP Pavilion ze4900 laptop with Ubuntu 7.10 Gutsy Gibbon installed and would LOVE to be able to use the cube desktop thing where you can switch around to different desktops in a 3D way. Someone told me to go into appearance and effects but it wont let me change from no effects. When I click on normal or extra I get "desktop effects could not be enabled". My HP came with a disk I used to have to install on windows that had the drivers for my graphics card but I cant install them now and I know the missing graphics accelerator driver might be the issue.

Can anyone help me out?

---

### Post by overdrank on 2008-01-06
> **hyp3rdrv said:**
> Hey guys, I am a complete noob to Linux but so far I love it - aside from a few issues.

I have an HP Pavilion ze4900 laptop with Ubuntu 7.10 Gutsy Gibbon installed and would LOVE to be able to use the cube desktop thing where you can switch around to different desktops in a 3D way. Someone told me to go into appearance and effects but it wont let me change from no effects. When I click on normal or extra I get "desktop effects could not be enabled". My HP came with a disk I used to have to install on windows that had the drivers for my graphics card but I cant install them now and I know the missing graphics accelerator driver might be the issue.

Can anyone help me out?

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by hyp3rdrv on 2008-01-06
kaleb@kaleb-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
kaleb@kaleb-laptop:~$

---

