---
title: "graphics issues *newb alert*"
date: 2009-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by McTwizle on 2009-06-21
I have a Dell Inspiron E1505 that I am learning linux with.  My first try with it is Ubuntu 9.04.  I have been trying to get everything set up on this laptop but am finding issues with the graphics.  In full screen its very choppy at best.  I have googled everything I can think of and have seen many suggestions but I get lost half way through the example because of my newbishness.  Here is what I have figured out with some commands I found somewhere in my google adventures.  The first is a hardware list (lspci).  The second is something to do with the graphics chip and the drivers its using I think (lshw -C display).  Does the display being unclaimed mean its not using the right driver ?  If so how do I make it use something better ?  Thanks for any help and patience with a newbers.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02

################################################################################

 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by coffeeaddict22 on 2009-06-22
Hi,
Welcome to Ubuntu!
The problem you've got is the graphics chipset. The Intel 945 graphics driver in the 9.04 kernel doesn't play nicely, especially it seems with some of the stuff they've done to the window manager part of Linux (Xorg).  If you google "Intel 945 graphics Linux", you'll get the hits.
There are ways around it.  The very latest kernel is one, or you can drop back to an older kernel.  A good post that defines the problems and some possible solutions is [here]("http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html"); post back if you want more help.

---

### Post by McTwizle on 2009-06-22
Does the Display being unclaimed mean I am not using the right driver ?  How do I know which one I am using ?  I have read about enabling EXA or UXA.  Do I have to manually do these or are they there by default ?  Do I just put them in there by editing Xorg.config and typing these in like I see in the examples ?  Here is what my file currently looks like.  Thanks for the help.


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerFlags"
    Option        "DontZap"    "off"
EndSection

---

### Post by coffeeaddict22 on 2009-06-23
Basically, get a cutting edge kernel.  It does autoupdate once you've got the source listed in Synaptic, and that'll get you working OK.  Without a driver that the kernel can talk to, you're not going to be able to get the display UNCLAIMED issue sorted.  The post I referred to in my last reply has instructions; they aren't a lot of fun to follow, so if you get stuck post back and I'm happy to walk you through the fun bits.
btw, this is my output from the lshw command:
```
~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Mobility Radeon HD 3650
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

```
The bottom line is the bit you're missing: you need a driver.
Any terminal command has a series of help files that give info about it; type "man xxxx" where xxxx is the command you're curious about and you'll get more info than you really wanted!

---

### Post by McTwizle on 2009-06-23
I am so lost.  I googled til my fingers hurt and followed the second part of the tutorial you linked to in the previous post.  I downloaded a driver from the intel site and tried to open it but dont know how to install.  I read the readme.txt on the site and it was very confusing to me.  Would be alot easier if I could just double click something but that would be the easy way out.  Once I have a driver downloaded how do I install it ?  I can open terminal and find information but that is the limit of my abilities as of now.  This is still fun to learn with but I think I am getting information overload and that makes me tend to run in circles.  I keep ending up back at this post searching for clues.  Any directions you would like to point me in ?  Thanks for the help so far.

---

### Post by Talon2 on 2009-06-24
> **McTwizle said:**
> I am so lost.

I recommend you go back to Ubuntu 8:10.  The Intel graphics problems are a result of a lot of work and bad timing.  Intel is making some big improvements to their graphics drivers but they have made a little mess in the mean time.  I suspect the problems will be cleaned up by 9.10 so I recommend you learn with 8.10 and look forward to using 9.10 when it comes out in October.

---

### Post by coffeeaddict22 on 2009-06-24
It's an option.

---

### Post by McTwizle on 2009-06-25
I have been contemplating that option.  From what I have been reading that sounds like a better starting point for me.  It is fun trying to fix this one up but maybe I would be better off learning in 8.10 first.  Thanks for all the help.  This is a valuable resource and I'm glad I found it.

---

### Post by McTwizle on 2009-07-09
I have gone back to 8.10 and am having the same issues.  Any ideas ?  I cant figure out what is being used for the driver.  With the display being unclaimed it doesn't seem to me that is is using the intel driver.  I dont know any linux people so online is my only resource.  Wish I could figure this out.

---

### Post by McTwizle on 2009-07-12
I have tried some different xorg.conf setups that I have copied online.  I still have the "Display 0:UNCLAIMED" in lshw -class display.  How do I fix this ?  Is it not using the right driver ?  Recently I tried opening FullTiltPoker and it updated.  I did a restart after it was done and now the program will not launch.  It comes up in the bottom of the panel and says starting fulltiltpoker and then it just dissappears.  Is there some type of log file I can look at and try to figure out why it is aborting ?  Here is an xorg.conf I am trying.


Section "Extensions"
  Option "Composite"
EndSection

Section "ServerFlags"
  AllowMouseOpenFail # allows the server to start up even if the mouse does not work
EndSection

Section "Module"
  Load "dbe" # Double-Buffering Extension
  Load "v4l" # Video for Linux
  Load "extmod"
  Load "type1"
  Load "freetype"
  Load "glx" # 3D layer
  Load "dri" # direct rendering
EndSection

Section "InputDevice"
  Identifier "Keyboard1"
  Driver "kbd"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "fr"
  Option "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
  Identifier "Mouse1"
  Driver "mouse"
  Option "Protocol" "ExplorerPS/2"
  Option "Device" "/dev/mouse"
EndSection

Section "InputDevice"
  Identifier "SynapticsMouse1"
  Driver "synaptics"
  Option "SHMConfig" "on"
EndSection

Section "Monitor"
  Identifier "laptop"
  Option "PreferredMode" "1280x800"
  Option "Below" "external"
EndSection

Section "Monitor"
  Identifier "external"
  Option "PreferredMode" "1680x1050@60"
  HorizSync 24.0 - 82.0
  VertRefresh 48.0 - 76.0
  Modeline "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -HSync +Vsync
EndSection

Section "Device"
  Identifier "device1"
  VendorName "Intel Corporation"
  BoardName "Intel 810 and later"
  Driver "intel"
  Option "DPMS"
  # Option "XaaNoOffscreenPixmaps" "1"
  Option "monitor-LVDS" "laptop"
  Option "monitor-VGA" "external"
EndSection

Section "Screen"
  Identifier "screen1"
  Device "device1"
  Monitor "external"
  Subsection "Display"
    Virtual 1680 1850
  EndSubsection
EndSection

Section "ServerLayout"
  Identifier "layout1"
  InputDevice "Keyboard1" "CoreKeyboard"
  InputDevice "Mouse1" "CorePointer"
  InputDevice "SynapticsMouse1" "AlwaysCore"
  Screen "screen1"
EndSection

---

