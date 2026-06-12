---
title: "Need opinion about xgl+compiz install!!!!"
date: 2006-09-07
forum: Desktop Environments
---

### Post by soutSA on 2006-09-07
Hello,

I had compiz-vannila installed and it was working great. Then I tried to do the compiz themer install and I ran into all sorts of problems. 

First I lost my title bars for my windows and then I did al sort of thing to try and correct it, and being some what of a newbie I broke it even more. Now I have reinstalled ubuntu dapper 6.06 and want to have another go at installing compiz.

I was looking at the following threads and was not sure witch one will be the best and if there is something better out there:

[www.ubuntuforums.org/showthread.php?t=244559&highlight=xgl+compiz](www.ubuntuforums.org/showthread.php?t=244559&highlight=xgl+compiz)
[www.ubuntuforums.org/showthread.php?t=131267&highlight=xgl+compiz](www.ubuntuforums.org/showthread.php?t=131267&highlight=xgl+compiz)


Here is my lspci output:

[HTML][SIZE="5"]0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:06:09.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:06:09.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:06:09.3 Mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:06:0a.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)[/SIZE]
[/HTML]

I am not sure if I have to go for the Nvidia or ATI install. Please point me in the right direction.

Thanks in advance

---

### Post by sylvester_0 on 2006-09-07
Good luck, I'm also trying out this magical thing called compiz. Judging from your lspci, you have an Intel integrated 915 video card. Follow the instructions on the first thread that you linked and you *should* be good. One thing that has changed recently is that all you have to do is run compiz-start and all the stuff will start up (window decorations, etc.) In the past this was done with a compiz plugins + gnome-window-decorator command. Good luck!

---

