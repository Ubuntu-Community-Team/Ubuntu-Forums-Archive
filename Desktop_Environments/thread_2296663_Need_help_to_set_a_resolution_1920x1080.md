---
title: "Need help to set a resolution 1920x1080"
date: 2015-09-27
forum: Desktop Environments
---

### Post by sergio47 on 2015-09-27
Hi, I recently installed Ubuntu gnome 14.04, and I'm trying to set a resolution of 1920x1080. My pc use a Nvidia gtx 660 OC, and in windows I can handle with this resolution perfectly.
I searched in google how to to this, and I found very similar tutorials of it. I followed instructions but it doesn't work. I put the command lines I used.

root@RASTUNTU:/home/rasteck# sudo cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

root@RASTUNTU:/home/rasteck# xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

root@RASTUNTU:/home/rasteck# sudo xrandr -q
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0x2b5)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

root@RASTUNTU:/home/rasteck# xrandr --addmode DVI-I-0 1920x1080_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40


I searched for this error, and I tried changing the name in quotes by "1080p", and still not working. Doesn't work any of the solutions I found.
Somebody can help me? Thank you ;)

---

### Post by dino99 on 2015-09-28
can you tell us how is plugged the display ? (dvi/hdmi/...) is a switch used ?
with linux systems, nowadays the kernel identify/set the found devices; so boot without xorg.conf file as it can hugely disturb the default system settings; and glance at xsession-errors for possible usefull comments to dig around your issue. /var/log/dmesg can be checked too.

---

### Post by matt_symes on 2015-09-28
Hi

What driver are you using ? Posting the output of this command will tell us.

```
sudo lshw -C display
```

I see you are using dvi-0. Have you tried a different connector such as hdmi ?

You can also try to use this command instead of cvt to get the mode lines.

```
gft
```

Reading the man page or web searching for the above command will give more information and it may give slightly different mode line values that you can try.

Kind regards

---

### Post by sergio47 on 2015-09-28
Hi, thanks for answering.

DIno99, I'm using a DVI in the graphic card, and VGA in the monitor. I will try what you say, will keep you informed.

Matt_symes, im using the NVIDIA binary driver 346.82, I post you the output of the commands. I cant use hdmi, because my screen only had VGA, the controller of the HDMI of my screen is broken and doesn't work. 

root@RASTUNTU:/home/rasteck# lshw -C display
  *-display               
       descripción: VGA compatible controller
       producto: GK106 [GeForce GTX 660]
       fabricante: NVIDIA Corporation
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: a1
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vga_controller bus_master cap_list rom
       configuración: driver=nvidia latency=0
       recursos: irq:30 memoria:f6000000-f6ffffff memoria:e8000000-efffffff memoria:f0000000-f1ffffff ioport:e000(size=128) memoria:f7000000-f707ffff

I will investigate about gtf function. But I dont know if, for change resolution, I need to use xrandr or something with the nvidia drivers and config files.

---

### Post by matt_symes on 2015-09-28
Hi

Try using xrandr again.

Do you have an xorg.conf file ? If you do then post it here.

Dino is correct when he stated that resolutions should be auto detected but it does not always work correctly. If you have an xorg.conf file, that may be causing you problems.

That being said, if you have no xorg.conf file and you still cannot get xrandr to add the resolution you are after then you may actually have to create an xorg file containing just monitor and screen sections. I have had to do this in the past to get a resolution I was after. That may or may not work for you.

Kind regards

---

### Post by sergio47 on 2015-09-28
Yes, I created an xorg.conf file to solved that. I heard that, resolutions should be detected automatically, but it doesn't work to me.
That is my xorg.conf file. Following some steps in this forum, I added this line to device.

    Option         "ModeValidation" "AllowNonEdidModes"

And that is the file:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 331.20  (buildd@roseapple)  Mon Feb  3 15:07:22 UTC 2014

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660"
    Option         "ModeValidation" "AllowNonEdidModes"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by matt_symes on 2015-09-28
Hi

I confused. Does the xorg.conf file in your last post work for you now ?

It has no mode line entries.

Kind regards

---

### Post by sergio47 on 2015-09-28
Hi
I don't know, I just generated the file in Nvidia settings, and try to modificate it. I think it will work.
Sorry, I don't know too much about this, I only know that this is used to control graphic card settings in case of autodetection fails and you need to do it manually, which is my case :(
Which mode line entries should I add?

Dino99, sorry, I forgot answer you. I tried restarting the computer without the file, but still not working.

---

### Post by matt_symes on 2015-09-29
Hi

You need to add modeline entries to the monitor section and then add references to then under the screen section.

That has worked for me in the past.
 
I'm not near my PCs at the moment but will post what worked for me tomorrow.

Kind regards

---

### Post by sergio47 on 2015-09-30
Ok, thank you :)

Anyway, I will investigate about this modelines, I should learn about that.

Regards.

---

