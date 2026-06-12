---
title: "Unable to configure Intrepid to max screen resolution"
date: 2009-01-14
forum: General Help
---

### Post by mixmaster on 2009-01-14
Under Hardy (using an old xorg.conf preserved from 7.04) I was able to persuade my IBM desktop machine (a Thinkcentre) to run at 1600x1200 on the IBM Thinkvision LCD monitor (200p).  Under Intrepid I have been unable to get it above 1152x864.

xrandr output (Intrepid)
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA disconnected (normal left inverted right x axis y axis)
TMDS-1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  

xrandr output (Hardy)
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 (normal left inverted right) 0mm x 0mm
   1600x1200      60.0* 
   1280x1024      75.0  
   1024x768       75.0  
   800x600        75.0  
   640x480        75.0  

lspci output (Intrepid or Hardy)
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)

It is rather frustrating that Dapper detected and configured this system perfectly and that the graphics have become progressively more problematic with each release.

---

### Post by pedro_orange on 2009-01-14
Whats your xorg.conf look like?

---

### Post by mixmaster on 2009-01-14
Currently it looks like this:
----------------------
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth 24
SubSection "Display"
        Modes "1600x1200"
EndSubSection
EndSection
-------------------
I added the Defaultdepth & the Display subsection in a futile attempt to get it to work

---

### Post by mixmaster on 2009-01-15
I'll bump this once in the hope someone has some idea.  If not I'll report it as a bug

---

