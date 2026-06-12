---
title: "Games don't work well in unity"
date: 2011-07-25
forum: Gaming &amp; Leisure
---

### Post by amitst on 2011-07-25
I was trying to play Warzone 2100 on 11.04. However I found that sometimes the game doesn't start. After running the game binary, the screen resolution changes to the one specified in the game. The game sound starts playing. However the currently running application (like Terminal, Firefox) continue to get displayed in the changed resolution. There is no new window for the game. The screen also freezes. I have to press Ctrl-Alt-F1 and start a new command line session to reboot (any other better ways to unfreeze are welcome).

In older Ubuntu versions, I used to disable the Compiz features and the games used to work well. Currently the only workaround for me is to start Ubuntu session in "Classic (no effects)" mode and play the games. Isn't there any better way to run games in Unity itself?

Also in the classic/no effects mode too I sometimes find that, after exiting the game, the resolution doesn't change back (it remains as 800x600 or 640x480). I have to manually set it back to say 1440x900.

Any tips for the two issues?

---

### Post by ubudog on 2011-07-25
Hmm... what graphics card are you using?  Also, have you installed any drivers for it after installing 11.04?

---

### Post by amitst on 2011-07-27
I haven't installed any specific driver. I will get back to you regarding the graphics card specification.

---

### Post by kaldor on 2011-07-27
You can find out which Graphics Card you have by running this command in a Terminal:

```
lspci
```

Find the line where it says "VGA compatible controller". In my case, it is this:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
**01:00.0 VGA compatible controller: ATI Technologies Inc NI Caicos [AMD RADEON HD 6450]**
01:00.1 Audio device: ATI Technologies Inc Device aa98
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```


Oh, and you can try Unity-2d. It is a stripped down version of Unity which does not need compiz. It does not have the flashy effects and other fun stuff, but it works. Relogin and choose it like any other session as "Unity 2D"

```
sudo apt-get install unity-2d
```

---

### Post by amitst on 2011-07-27
Thanks for supplying the command. Here are the graphics card details,

```

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

```

I will check unity-2d and let you know

---

### Post by amitst on 2011-07-27
Yes, using unity-2d seemed to have resolved the issue. Thanks for the support.

---

