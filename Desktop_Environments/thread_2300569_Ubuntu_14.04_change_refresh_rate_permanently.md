---
title: "Ubuntu 14.04: change refresh rate permanently"
date: 2015-10-26
forum: Desktop Environments
---

### Post by erotavlas on 2015-10-26
Hi,
I want to set the refresh rate for an old CRT display on my ubuntu 14.04 64 bit. I read here [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) and I can successfully change the refresh rate with the command
```

 xrandr --output VGA1 --mode 1280X1024 --rate 85

```
However, I cannot made the setting permanent even if I modified the file ~/.xprofile by adding the previous line. I also tried to make the file executable with chmod.
Any suggestions?

---

### Post by RockDoctor on 2015-10-26
Generate the required modeline:```
~$ gtf 1280 1024 85

  # 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
```
Then place the modeline generated above in an an appropriate config file in /etc/X11/xorg.conf.d (the file below is set up for my old Soyo monitor; change DisplaySize, HorizSync, and VertRefresh as necessary for your monitor):
```
cat /etc/X11/xorg.conf.d$ cat 10-my_monitor.conf 
Section "Monitor"
  Identifier   "Monitor0"
  VendorName   "Soyo"
  ModelName    "DYLM2086"
  DisplaySize  432  270
  HorizSync    30.0 - 86.0
  VertRefresh  56.0 - 76.0
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
  Option      "PreferredMode" "1280x1024_85.00"
EndSection
```

---

### Post by erotavlas on 2015-10-27
> **RockDoctor said:**
> Generate the required modeline:```
~$ gtf 1280 1024 85

  # 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
```
Then place the modeline generated above in an an appropriate config file in /etc/X11/xorg.conf.d (the file below is set up for my old Soyo monitor; change DisplaySize, HorizSync, and VertRefresh as necessary for your monitor):
```
cat /etc/X11/xorg.conf.d$ cat 10-my_monitor.conf 
Section "Monitor"
  Identifier   "Monitor0"
  VendorName   "Soyo"
  ModelName    "DYLM2086"
  DisplaySize  432  270
  HorizSync    30.0 - 86.0
  VertRefresh  56.0 - 76.0
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
  Option      "PreferredMode" "1280x1024_85.00"
EndSection
```

Hi,
thank you for your fast reply. I get the same output as you
```

gtf 1280 1024 85

  # 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync

```
Then I created the following file /etc/X11/xorg.conf
```

Section "Monitor"
  Identifier   "Monitor0"
  VendorName   "LG"
  ModelName    "F900B"
  DisplaySize  432  270
  HorizSync    30.0 - 86.0
  VertRefresh  56.0 - 76.0
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
  Option      "PreferredMode" "1280x1024_85.00"
EndSection

```

My video card is intel i915
```

lspci -v -s `lspci | awk '/VGA/{print $1}'`
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at fea00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at cc00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

```
I forgot to say that I do not use unity, but classical gnome interface with gnome-session-fallback installation.

---

### Post by erotavlas on 2015-11-10
Hi,
I'm still looking to solve the refresh problem. Do you have any further suggestion?
Thank

---

### Post by RockDoctor on 2015-11-10
I placed the script below on my bootable flash drive to allow me to quickly set the resolution when using the USB stick on my desktop computer (I placed a link on the desktop and ran it from there). It's not quite what you were looking for, but I found it convenient. Hope this helps.
```

~/bin$ cat xrandr_helper 
#!/bin/bash

# A script to set up a new mode
# version 1 20150603
# version 2 add check for three parameters
# version 3 use zenity to enter parameters for gtf
# RockDoctor 20150605

# get parameters for gtf
hvf=$(zenity --forms --title="Screen Resolution Setter" \
             --separator=" " \
             --add-entry="# of Horizontal pixels: " \
             --add-entry="# of Vertical pixels: " \
       -     --add-entry="Frequency: ")
echo $hvf

# get the modeline from gtf
modeline=$(gtf $hvf)
modeline=$(echo "$modeline" | tail -n 1)
echo "modeline = $modeline"

# strip mode name from modeline
modeline_sans_name=$(echo $modeline | awk '{$1=""; $2="";print}')
echo "modeline_sans_name = $modeline_sans_name"

# create new mode name
mode="${1}x${2}"
echo "mode = $mode"

# now we adapt my old xrandr_1680x1050.sh script
#xrandr --newmode 1680x1050 147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
#xrandr --addmode $screen 1680x1050
#xrandr --output $screen --mode 1680x1050

# get name of screen
screen=$(xrandr | grep \ connected | awk '{print $1}')
echo "$screen"

# notify xrandr of new mode
newmode1="xrandr --newmode $mode $modeline_sans_name"
$newmode1
echo "newmode1 = $newmode1"

# made new mode accessible to $screen
newmode2=$(xrandr --addmode $screen $mode)
$newmode2
echo "newmode2 = $newmode2"

# switch to new mode
mode_switch=$(echo "xrandr --output $screen --mode $mode")
# uncomment the following line to implement resolution switching
$mode_switch
echo "mode_switch = $mode_switch"

```

---

