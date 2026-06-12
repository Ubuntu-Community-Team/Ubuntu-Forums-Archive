---
title: "Command line users please help me with terminal"
date: 2014-10-09
forum: Desktop Environments
---

### Post by mitchd123 on 2014-10-09
I have a strange problem that I've never seen in Linux.   The text in a terminal windows starts bouncing up and down.   If I move the terminal window somewhere else on the desktop the text will stop moving.  When I enter another command, it's starts moving again.   It's really annoying.   Resizing the terminal window and changing font sizes has no impact on the problem.  

A video is worth 100 words so let me show you what I mean. Here's a 10 second video of the problem   [http://youtu.be/gjBI-cRhNvg](http://youtu.be/gjBI-cRhNvg)

---

### Post by Impavidus on 2014-10-10
Seems a graphics driver problem to me. If you post some info on your graphics, someone may be able to help.

---

### Post by mitchd123 on 2014-10-13
Thank you for your response. You are correct, it was related to the video driver.   Consider this at least partially solved...I have the prime suspect.  


  I've updated my GForce 8400 GS  to the latest NVidia 64 bit driver (currently NVIDIA-Linux-x86_64-340.46 )   I was previously running NVIDIA-Linux-x86_64-331.20.    The problem has greatly improved but I'm still able to recreate it.  

I can live with it now.   I can get about 10 commands out before having to move the terminal window.    

# nvidia-settings:  version 340.46  (buildmeister@swio-display-x86-rhel47-03)  Wed Sep 24 14:38:19 PDT 2014

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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSP HSG1075"
    HorizSync       31.0 - 75.0
    VertRefresh     59.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "1920x1200 +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

