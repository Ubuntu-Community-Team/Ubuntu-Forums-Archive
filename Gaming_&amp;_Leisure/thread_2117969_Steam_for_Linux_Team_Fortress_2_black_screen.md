---
title: "Steam for Linux: Team Fortress 2 black screen"
date: 2013-02-19
forum: Gaming &amp; Leisure
---

### Post by xSCCMx on 2013-02-19
Hi,

I am currently having an error where Team Fortress 2 on Steam that recently came out of BETA has launched, played the valve symbol with a blank screen, overlay becomes available and then the program closes.

Could anyone tell me what this is?


Dell Inspiron 1520
Ubuntu 12.04.2 -ish

---

### Post by Perfect Storm on 2013-02-19
Some more info is needed.

More specs like video card, RAM etc.
Which version of Ubuntu do you use and if it's 32-bit or 64-bit.
Eventually have you tried starting the game up though the terminal to check for error output.

---

### Post by xSCCMx on 2013-02-19
Does this help? This is the my system specs according to Steam.
 I got lost after I fixed an error when it would not start at all.



Processor Information: 
    Vendor:  GenuineIntel 
    Speed: 1467 Mhz 
    2 logical processors 
    2 physical processors 
    HyperThreading:  Unsupported 
    FCMOV:  Supported 
    SSE2:  Supported 
    SSE3:  Supported 
    SSSE3:  Supported 
    SSE4a:  Unsupported 
    SSE41:  Unsupported 
    SSE42:  Unsupported 
     
Network Information: 
    Network Speed:   
     
Operating System Version: 
    Ubuntu 12.04.2 LTS (32 bit) 
    Kernel Name:  Linux 
    Kernel Version:  3.2.0-38-generic-pae 
    X Server Vendor:  The X.Org Foundation 
    X Server Release:  11103000 
    X Window Manager:  Compiz 
    Steam Runtime Version:  <Runtime enabled> 
     
Video Card: 
    Driver:  Intel Open Source Technology Center Mesa DRI Intel(R) 965GM x86/MMX/SSE2 
 
    Driver Version:  2.1 Mesa 9.0 
    Desktop Color Depth: 24 bits per pixel 
    Monitor Refresh Rate: 60 Hz 
    VendorID:  0x8086 
    DeviceID:  0x2a02 
    Number of Monitors:  1 
    Number of Logical Video Cards:  1 
    Primary Display Resolution:  1280 x 800 
    Desktop Resolution: 1280 x 800 
    Primary Display Size: 13.03" x 8.15"  (15.35" diag) 
                                            33.1cm x 20.7cm  (39.0cm diag) 
    Primary VRAM Not Detected 
     
Sound card: 
    Audio device: SigmaTel STAC9205 
     
Memory: 
    RAM:  2509 Mb 
     
Miscellaneous: 
    UI Language:  English 
    LANG:  en_US.UTF-8 
    Microphone:  Not set 
    Total Hard Disk Space Available:  72609 Mb 
    Largest Free Hard Disk Block:  48554 Mb 
     
Installed software: 
     
Recent Failure Reports:

---

### Post by Perfect Storm on 2013-02-19
You have an Intel 9xx card.
You may take a look at this, if you haven't already; [https://wiki.ubuntu.com/Valve#Intel_Graphics](https://wiki.ubuntu.com/Valve#Intel_Graphics)

---

### Post by xSCCMx on 2013-02-19
I am still getting a black screen and said problems despite looking and entering those intel commands.

I think my problem maybe this.
I may need an multi arch alternative.
sudo apt-get install libgl1-mesa-glx:i386

---

### Post by Perfect Storm on 2013-02-19
> **xSCCMx said:**
> I am still getting a black screen and said problems despite looking and entering those intel commands.

I think my problem maybe this.
I may need an multi arch alternative.
sudo apt-get install libgl1-mesa-glx:i386

If you haven't already installed 32-bit libs to your system:
```
sudo apt-get install ia32-libs
```
This package makes sure you get the 32-bit libs.

---

### Post by xSCCMx on 2013-02-19
I'l take a look at that when I have the chance.

---

### Post by R33D3M33R on 2013-02-20
You should try to run the game with the -novid parameter.

---

### Post by xSCCMx on 2013-02-20
I figured out that my version of OpenGL is not sufficient foe my hardware. TF2 requires version 3 and I have 2.1, unless Valve adds support for 2.1 we are going to be stuck with a black screen, Thank you Mod AI.

---

