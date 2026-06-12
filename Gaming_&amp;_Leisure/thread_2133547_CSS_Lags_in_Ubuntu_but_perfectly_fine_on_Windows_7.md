---
title: "CSS Lags in Ubuntu but perfectly fine on Windows 7 ?! Am I missing drivers?!"
date: 2013-04-08
forum: Gaming &amp; Leisure
---

### Post by Psil0cybin on 2013-04-08
Hey guys Just got Steam for ubuntu and CSS.
I have been playing it on my HP G62 laptop for years using windows 7
Decided to format and run Ubuntu full time, but the problem is when Ever I play CSS
The frame rate is horrible, everything is slow and I lag and the game is barely playable...while on Windows 7 It ran flawlessly.
What can be done to fix this? AM I missing drivers?
Jockey says I have no updates as I tried to go to additional drivers.
I found the AMD Video Card Driver I need off the AMD site but I have hessitent to install it and cause too many problems

What do you guys think?
Thanks in advance
Psil0

> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)




> 01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] (prog-if 00 [VGA controller])    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=64K]
    Memory at f0200000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon


01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]




Is this what I should follow?
[http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-driver-in-12-04-lts](http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-driver-in-12-04-lts)
I just want to make sure I dont cause to many problems

---

### Post by efflandt on 2013-04-08
With italics I cannot tell if your video says RS880M or R5880M (letter S or five?), but it also says Radeon HD 4200 Series, and Ubuntu no longer has accelerated video support for ATI 4000 series or earlier. Maybe someone knows if Ubuntu 12.04.2 would work any better.

I know that something major changed in 12.10 graphics, because when I tried 12.10 from a USB hard drive, the default nouveau driver was sluggish with nvidia, and even when I installed nvidia drivers, Dash was sluggish in populating itself with icons. 12.10 graphics was also sluggish in virtualbox, but I have not tried that since a couple of virtualbox updates because I needed disk space for Linux Steam games in 12.04 (mostly tf2, but I did buy Half-Life and CSS when they were discounted).

---

### Post by Psil0cybin on 2013-04-08
Sorry about the Italics
Its an 'S'
VGA compatible controller: Advanced Micro Devices [AMD] nee **ATI** **RS880M** [ Mobility Radeon HD 4200 Series ]

Does this mean I am out of luck? And that CSS and all Source games will be unplayable, due to the fact that Ubuntu no longer has accelerated video support for ATI 4000? 
darn so what is my best bet? could anything be done? Would downloading that driver from ATI be a bad call?
Or could it fix that issue?
I tried downloading Catalyst Control Manager like i had on Windows, but it also didn't find my driver and said it was unsupported, when I ran the same program on Windows 7
Thanks again in advance.

---

### Post by Perfect Storm on 2013-04-09
To clear up some things: Ubuntu did not abandoned your card. ATI/AMD doesn't support older cards (restricted drivers). They tend to abandoned them when releasing new cards.
You could try updating the open source driver and see if it helps -

Open the terminal;

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mastablasta on 2013-04-09
or use 12.04 which still has support for your card
or downgrade the xserver as last resort.

---

### Post by Psil0cybin on 2013-04-10
> **mastablasta said:**
> or use 12.04 which still has support for your card
or downgrade the xserver as last resort.

I'm already using 12.04
So is the top option technically my only option?

---

### Post by mastablasta on 2013-04-11
install AMD proprietary drivers then.

---

### Post by Psil0cybin on 2013-06-08
Which drivers would that be? Sorry I just am new to linux somewhat so I want to make sure my GUI Desktop doesn't encounter any problems after any updates.
What do you guys recommend for my situation? Is their a specific driver I am missing? or is outdated? Maybe someone can guide me so I do not cause to many problems?

> **Artificial Intelligence said:**
> To clear up some things: Ubuntu did not abandoned your card. ATI/AMD doesn't support older cards (restricted drivers). They tend to abandoned them when releasing new cards.
You could try updating the open source driver and see if it helps -

Open the terminal;

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
```

Would following the above commands be of any help? Using OpenSource Drivers? Or with any kind of driver fiddling I am prone to errors?
I just want to get the same experience from playing games on Windows 7 and Ubuntu due to the fact that there is clearly a difference in how games can be played, I am sure I can get more out of my current specs..Thanks in advance

---

### Post by mastablasta on 2013-06-09
as mentioned AMD abandoned the chips. i am not sure why they also did it in middle of 12.04 which is what it seems have happened. anyway if you look at the download page you can find an older version 12.04.1 - which should work well with your card and should offer you to install drivers.

the issue is that ubuntu added new xserver and kernel with 12.04.2 to enable newer hardware to work on LTS. but AMD didn't update the legacy card to support the new xserver. however if you install older version of 12.04 you will keep the older kernel and older xserver which will work fine with your hardware. this is a solution until the opensource drivers improve. 

the solution provided with mentioned commands will update your opensource drivers to latest version. since you use 12.04 and we are at 13.04 now you will get an updated version (same as in 13.04 i believe) of opensource drivers which might solve your issue. you can remove the PPA later if necessary. and the only thing this deals with is display. so if you run into some problems you can remove this PPA. it pays to have a live USB /DVD prepared in case you might need it to access the internet.

---

### Post by Psil0cybin on 2013-06-12
Thank you so much that's exactly what I think I might do , or try.
Thanks again, for getting back to me..

---

### Post by cRaZyBisCuiT on 2013-06-12
Is it working? It's only a question of the driver. The ati legacy drivers do work up to kernel 3.2, 3.5 (LTS enabled stack) does not work as far as I know. Btw nVidia does the same thing. The only difference ist, that they support their cards for a longer period of time.

---

