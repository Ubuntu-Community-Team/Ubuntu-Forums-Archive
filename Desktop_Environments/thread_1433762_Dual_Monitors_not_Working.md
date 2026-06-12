---
title: "Dual Monitors not Working"
date: 2010-03-19
forum: Desktop Environments
---

### Post by kierpaul on 2010-03-19
Hello everyone! I have an HP Laptop Pavilion ze4800 that is running an ATI Mobility Driver 320m. Kind of old. I could not get dual monitors working with this thing for some reason. Could anyone help me? When I start this thing up I can see it on both screens, but as soon as it gets to the login screen, my other monitor goes blank off the VGA. What is weird is that the laptop sees it, but it is like it is not transmitting to it. I am using version 9.10 and I have posted lspci, xrandr, and xorg.conf below. Any help is greatly appreciated!

 lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
bob@bob-laptop ~ $ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 connected (normal left inverted right x axis y axis)
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)
bob@bob-laptop ~ $ 


**xorg.conf**

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by kierpaul on 2010-04-01
These old ATI cards are hard to get support for and ATI does not even support this type of card anymore. I was trying to convince a fellow Linux was the way to go.....I failed miserably because of a stupid graphics card. If I did manipulate the xorg file, every time there was an upgrade to a different distribution I would have to make sure that this file was kept safe! Impossibility for me! Users are not going to want to manipulate an xorg file to make their computer work....this is not the fault of Linux though.....he had to go back to Windows! If only ATI would open source their drivers!

---

### Post by www.rzr.online.fr on 2012-07-05
> **kierpaul said:**
>  If only ATI would open source their drivers!

igp320m is using radeon opensource driver ...

---

### Post by overdrank on 2012-07-05
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

