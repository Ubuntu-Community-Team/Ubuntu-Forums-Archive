---
title: "Display properties say Monitor: Unknown"
date: 2010-10-29
forum: Desktop Environments
---

### Post by virtualexplorer on 2010-10-29
hi,
I have been using ubuntu past 1yr. The display properties have never detected my monitor ... so many problems occur while viewing webpages, the fonts are too small, online games too look small, pages dont scroll smoothly and so on.

I have tried Openchrome (Currently installed), have tried Nvidia (crashes). My motherboard have via chipsets (Via K8M800-CE + VT8237R) (K8MM-V)

Yesterday I upgraded to Ubuntu 10.10 and my system is upto date ...have applied all updates available from the update manager. I have read about them a lot and googled a lot but didnt find any solution.
Hope to get the display fixed here ... :)

Thanks in advance

---

### Post by virtualexplorer on 2010-10-30
Any one?? Or is this a bug that does not have a fix yet??

---

### Post by virtualexplorer on 2010-10-31
:( I need to fix it plz help ..

---

### Post by theonhighgod on 2010-12-27
I'm having an issue with getting above 800x600 resolution on this chipset, don't suppose you've had any luck?

lspci reports:
```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

```
"sudo lshw -C video" gives :
```
-display UNCLAIMED     
       description: VGA compatible controller
       product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2
       resources: memory:f0000000-f3ffffff memory:f4000000-f4ffffff memory:f5000000-f500ffff

```

this the same sort of output as you get?

---

### Post by realzippy on 2010-12-27
Necroposting...member *virtualexplorer* 
is not active on the forum since October.
Basically you have to create an xorg.conf file and add the resolution there.
Which Ubuntu version ?(AFAIK VIA made a driver,but this does not work on newer Xserver used by 10.10...)

---

### Post by theonhighgod on 2010-12-27
found this and it helped a lot [http://www.uluga.ubuntuforums.org/showthread.php?t=1648607](http://www.uluga.ubuntuforums.org/showthread.php?t=1648607)

> **davidmohammed said:**
> I agree - not fun

maybe try to manually get the openchrome driver to recognise the screen resolution you want e.g.

If you run:
gksudo gedit /etc/X11/xorg.conf
and paste this text:


```
Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection
Section "Monitor"
 Identifier "Configured Monitor"
 Option "DPMS"
 HorizSync 28-80
 VertRefresh 43-60
EndSection
Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1024x768"
 EndSubSection
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

```

Save the file, close gedit and reboot. If the new setting is bad you can boot to root recovery mode and rename the file.

all i had to do was log off and the resolution was ok, not yet the optimum for my monitor

---

### Post by theonhighgod on 2010-12-27
my monitor has a resolution of 1280x1024 i was able to change this using the "monitors" options found in system under preferences, i then set it to default.

I also had a problem with Plymouth (The program that should produce a nice graphical loading screen, or in this case created a psychedelic largely light purple scrolling diagonal line screen before reaching the login screen) to solve this there's two options, install startup-manager and untick the show boot splash button, or i think uninstalling the plymouth-theme-ubuntu-logo package would do the same thing.


good luck

---

### Post by virtualexplorer on 2010-12-29
Finally, a reply after whole two months ... lol
M still searching for a solution .. i even had a chat with some one on the #ubuntu channel on freenode irc, but none was able to help me to my satisfaction. Further i read, that via Technologies themselves are not providing drivers for Linux (Ubuntu). Also read, who ever wants the best out of ubuntu shld not install it on a via chipset computer.... :(
There can be a solution but just have to do trial n error stuff. I have tried openchrome drivers and also some via drivers ... there was no change in the current situation

---

