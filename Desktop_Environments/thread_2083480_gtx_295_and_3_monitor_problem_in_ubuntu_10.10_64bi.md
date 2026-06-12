---
title: "gtx 295 and 3 monitor problem in ubuntu 10.10 64bit"
date: 2012-11-12
forum: Desktop Environments
---

### Post by efeefeefe on 2012-11-12
(Ubuntu 12.10 sorry for wrong title i cant edit that)
Hi, this is my first linux experince and im learning a bit slowly.  I need your help.

i used this commands: 
  sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
        sudo apt-get update 
        sudo apt-get install nvidia-current

and after restarting, ubuntu now working more good but my third monitor is not working and  there is only two monitor in the desktop setting screen.

nvidia-xconfig --query-gpu-info

Number of GPUs: 2

GPU #0:
  Name      : GeForce GTX 295
  PCI BusID : PCI:4:0:0

  Number of Display Devices: 1

  Display Device 0 (DFP-0):
      EDID Name             : Philips 244E
      Minimum HorizSync     : 30.000 kHz
      Maximum HorizSync     : 83.000 kHz
      Minimum VertRefresh   : 56 Hz
      Maximum VertRefresh   : 76 Hz
      Maximum PixelClock    : 170.000 MHz
      Maximum Width         : 1920 pixels
      Maximum Height        : 1080 pixels
      Preferred Width       : 1920 pixels
      Preferred Height      : 1080 pixels
      Preferred VertRefresh : 60 Hz
      Physical Width        : 520 mm
      Physical Height       : 290 mm


GPU #1:
  Name      : GeForce GTX 295
  PCI BusID : PCI:5:0:0

  Number of Display Devices: 2

  Display Device 0 (DFP-0):
      EDID Name             : Philips 231S
      Minimum HorizSync     : 30.000 kHz
      Maximum HorizSync     : 83.000 kHz
      Minimum VertRefresh   : 56 Hz
      Maximum VertRefresh   : 76 Hz
      Maximum PixelClock    : 170.000 MHz
      Maximum Width         : 1920 pixels
      Maximum Height        : 1080 pixels
      Preferred Width       : 1920 pixels
      Preferred Height      : 1080 pixels
      Preferred VertRefresh : 60 Hz
      Physical Width        : 510 mm
      Physical Height       : 290 mm

  Display Device 1 (DFP-1):
      EDID Name             : Samsung SyncMaster
      Minimum HorizSync     : 30.000 kHz
      Maximum HorizSync     : 81.000 kHz
      Minimum VertRefresh   : 56 Hz
      Maximum VertRefresh   : 75 Hz
      Maximum PixelClock    : 150.000 MHz
      Maximum Width         : 1680 pixels
      Maximum Height        : 1050 pixels
      Preferred Width       : 1680 pixels
      Preferred Height      : 1050 pixels
      Preferred VertRefresh : 60 Hz
      Physical Width        : 470 mm
      Physical Height       : 300 mm


i tried this command:   
nvidia-xconfig --base-mosaic --metamodes="GPU-0.DFP-0: 1680x1050+0+0, GPU-1.DFP-0: 1680x1050+3360+0, GPU-0.DFP-1: 1680x1050+5040+0"

WARNING: Unable to locate/open X configuration file.

Option "BaseMosaic" "True" added to Screen "Screen0".

ERROR: Unable to write to directory '/etc/X11'.

What can i do now? i can open "NVIDIA X Server Settings" 
but i dont know how to save  
where do i need to save and what file name?
/usr/share/X11/xorg.conf.d ?
please help
best regards,
Efe

---

