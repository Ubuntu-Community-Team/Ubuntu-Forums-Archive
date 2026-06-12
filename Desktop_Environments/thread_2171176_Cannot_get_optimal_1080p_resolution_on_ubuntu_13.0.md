---
title: "Cannot get optimal 1080p resolution on ubuntu 13.04"
date: 2013-08-29
forum: Desktop Environments
---

### Post by George_Kourouleas on 2013-08-29
Hello to everybody. My problem is the following one:

I cannot get 1920x1080 resolution on Ubuntu 13.04 . I have tried 12.04 and 12.10 as well and I am trying right now to set a custom resolution with xrandr command but that fails for a reason.
I have tried all the possible solutions from this forum for a week now but I cannot manage to get to the right solution so any help would be highly appreciated.

My graphics card is ATI Radeon 7850 .
My monitor is a Samsung SyncMaster S22B150 model.

Output of xrandr : 
```

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 disconnected (normal left inverted right x axis y axis)
DFP6 disconnected (normal left inverted right x axis y axis)
DFP7 disconnected (normal left inverted right x axis y axis)
DFP8 disconnected (normal left inverted right x axis y axis)
DFP9 disconnected (normal left inverted right x axis y axis)
DFP10 disconnected (normal left inverted right x axis y axis)
DFP11 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        59.9
```

Then, I type cvt and I add the 1920x1080 resolution.

```
$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

Then, 

```
$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```


Then, I have an error 
```
$ xrandr --addmode $ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  141 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  57
  Current serial number in output stream:  57

```


Finally, here is my xorg.conf with sudo gedit:
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

lspci output :

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] FCH SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:16.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Pitcairn PRO [Radeon HD 7850]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)

```

---

### Post by lah7 on 2013-08-29
Hello, welcome to the forums! I believe you're using ATI's proprietary driver. By any chance, have you tried the open source driver 'out-of-the-box' one?

In my experience I haven't had much luck with ATI's Linux drivers so I've always used Nvidia's graphics cards. Sorry I'm not much help here. :(

---

### Post by George_Kourouleas on 2013-08-29
Thanks for your answer lah7.  Yes, I have downloaded and installed the AMD Catalyst™ Proprietary Display Driver - Linux x86 & Linux x86_64 .

About the open source driver, I believe that by default Ubuntu will use the open source AMD or Radeon driver  for cards manufactured by AMD. So, I have tried that a lot as well.

I believe that it comes down to the right configuration of xorg.conf , but I am yet to configure it properly so that I will have 1920 x 1080 resolution.

Whoever knows about this, please help me because Ubuntu is my primary OS and I am doing serious work with it. Thanks in advance. :)

> **lah7 said:**
> Hello, welcome to the forums! I believe you're using ATI's proprietary driver. By any chance, have you tried the open source driver 'out-of-the-box' one?

In my experience I haven't had much luck with ATI's Linux drivers so I've always used Nvidia's graphics cards. Sorry I'm not much help here. :(

---

### Post by SeijiSensei on 2013-08-29
How are you connecting to the monitor?  With an HDMI cable or VGA?  You may not get the same resolutions using one method versus the other.  On the machine I'm using now, with a similar Radeon card, I had to enter the BIOS and force the machine to choose the ATI adapter (called "fixed" mode on my HP) since it has a hybrid design.  I use an HDMI cable to connect it to my Sony Bravia HDTV and can push it to 1080p in that arrangement.

---

### Post by George_Kourouleas on 2013-08-29
Hello. Since my monitor has only a VGA output(neither dvi, nor hdmi) I use this VGA output from the screen and I use a VGA to DVI adapter on my graphics card end.
I was thinking that maybe that was the problem and there is no way of forcing 1080p resolution with something else besides HDMI(digital sign).
So, now that I have VGA cable do you think that is possible for me to force a 1080p resolution?

Regards, George.

> **SeijiSensei said:**
> How are you connecting to the monitor?  With an HDMI cable or VGA?  You may not get the same resolutions using one method versus the other.  On the machine I'm using now, with a similar Radeon card, I had to enter the BIOS and force the machine to choose the ATI adapter (called "fixed" mode on my HP) since it has a hybrid design.  I use an HDMI cable to connect it to my Sony Bravia HDTV and can push it to 1080p in that arrangement.

---

### Post by WrTtxyK on 2013-08-29
Try adding HorizSync and VertRefresh rates on your xorg.conf's Section "Monitor"

---

### Post by SeijiSensei on 2013-08-30
> **George_Kourouleas said:**
> So, now that I have VGA cable do you think that is possible for me to force a 1080p resolution?

I believe it depends on the monitor.  You might want to read the specs and manual for yours again and see what analog resolutions it supports.  

Does this computer also boot Windows?  Can you get 1080p from a Windows session but not Linux?

---

### Post by George_Kourouleas on 2013-08-30
> **SeijiSensei said:**
> I believe it depends on the monitor.  You might want to read the specs and manual for yours again and see what analog resolutions it supports.  

Does this computer also boot Windows?  Can you get 1080p from a Windows session but not Linux?

Yes, on Windows I have a 1920x1080 resolution, but in the monitor's menu as well it sais that 1080p is the optimal analysis and the current one is 1600x1200.

>  Try adding HorizSync and VertRefresh rates on your xorg.conf's Section "Monitor" 

As for this, I am going to search & try this and then post the results.

The problem is, that, in xorg.conf when I try to force a 1080p resolution there, nothing happened.

---

### Post by George_Kourouleas on 2013-08-30
> **WrTtxyK said:**
> Try adding HorizSync and VertRefresh rates on your xorg.conf's Section "Monitor"

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    HorizSync 30 - 50
    VertRefresh 60 - 60 
EndSection

does not seem to do the work for me after a reboot. Maybe different values, but I do not know what value to put.

---

### Post by George_Kourouleas on 2013-09-12
Several days been passed. 
Should i **bump **the post?
Need help with this. 
Still unsolved. Appreciate it.

---

