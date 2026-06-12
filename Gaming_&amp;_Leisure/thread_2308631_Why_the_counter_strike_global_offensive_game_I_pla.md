---
title: "Why the counter strike global offensive game I play with very low fps"
date: 2016-01-04
forum: Gaming &amp; Leisure
---

### Post by muratsiradisi on 2016-01-04
[COLOR=#212121][FONT=arial]counter strike global offensive game I play with very low fps
[/FONT][/COLOR][FONT=inherit]
Do I need to develop hardware to play with better fps?
[/FONT][FONT=inherit]Can the software be able to make a better setting?
[/FONT]


glxinfo | grep "OpenGL version"

```
OpenGL version string: 4.5.0 NVIDIA 352.63


```

lspci

```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 730] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

```

[ATTACH=CONFIG]266552[/ATTACH]
[ATTACH=CONFIG]266553[/ATTACH]
[ATTACH=CONFIG]266554[/ATTACH]
[ATTACH=CONFIG]266555[/ATTACH]
[ATTACH=CONFIG]266556[/ATTACH]

---

### Post by QIII on 2016-01-04
Please do not use such large images.  Use the attachment functionality (the paper clip above the text entry box) to insert attachments, which will show the images as thumbnails.  Alternatively, use only the url.

Many Forums users have slow connections or data transfer caps which may be exceeded.

Thanks.

---

### Post by mastablasta on 2016-01-05
a setting seems to be off. the hardware is more than capable of running this game.

---

### Post by muratsiradisi on 2016-01-05
what should I do? Can you help me?

---

### Post by mastablasta on 2016-01-05
wish I could help you but I couldn't even get the GT 730 installed (had to return it) and I don't know much about NVidia chips. if you can't wait you can also ask on their forums. they will be able to help with the proper settings for this chip. something looks as if it's off as this hardware should easily run the game.

can you see if the load is on GPU or CPU? can you see what is responsible for poor performance? is the FPS improved if you reduce the screen resolution?

---

### Post by oldrocker99 on 2016-01-06
An nVidia 730 is not going to work very well for any graphics-intensive game, I'm afraid. These days, the *minimum* nVidia controller is at least the 750ti, or the new 950. Needless to say, you should reduce the settings to the lowest resolution, and turn off **all** the graphics extras (FSAA, shadows, etc.). It takes a pretty high-end card to run the game at even 1600x900, and the 730 isn't it.

A sweet spot for low-end graphics cards is from about $125-150, which will get you  the 750ti or the 950, which is the best way to solve your problem. It looks like that to me, at least.

---

### Post by mastablasta on 2016-01-07
pffft it's all in the settings. plenty of games work on my old radeon hd 3650 which is a lot weaker than this NVidia with a lot less and slower GPU RAM. just not at their highest setting I am not sure what global offensive is based on but it it is still on HL2 engine then I bet I could run it at some setting. and NVidia could do so as well.

---

