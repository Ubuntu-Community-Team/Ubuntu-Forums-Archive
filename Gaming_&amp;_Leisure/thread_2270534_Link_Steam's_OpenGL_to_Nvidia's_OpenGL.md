---
title: "Link Steam's OpenGL to Nvidia's OpenGL"
date: 2015-03-23
forum: Gaming &amp; Leisure
---

### Post by coughlin26 on 2015-03-23
Civilization 5 won't launch on my new machine, and the problem seems to be with OpenGL being too old. Steam starts fine, but when I click Start on Civ 5 I get a brief Steam Starting window and then nothing happens. Steam seems to think I'm on 1.4, but when I check OpenGL with glxinfo I'm on 4.4.

Here is the output of glxinfo | grep OpenGL:

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 750 Ti/PCIe/SSE2
OpenGL core profile version string: 4.4.0 NVIDIA 346.47
OpenGL core profile shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 346.47
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 NVIDIA 346.47
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:

And here is the output of Steam's System Information:

Processor Information:
    Vendor:  GenuineIntel
    CPU Family:  0x6
    CPU Model:  0x3c
    CPU Stepping:  0x3
    CPU Type:  0x0
    Speed:  3900 Mhz
    4 logical processors
    4 physical processors
    HyperThreading:  Unsupported
    FCMOV:  Supported
    SSE2:  Supported
    SSE3:  Supported
    SSSE3:  Supported
    SSE4a:  Unsupported
    SSE41:  Supported
    SSE42:  Supported
    
Network Information:
    Network Speed:  
    
Operating System Version:
    Ubuntu 14.10 (64 bit)
    Kernel Name:  Linux
    Kernel Version:  3.16.0-31-generic
    X Server Vendor:  The X.Org Foundation
    X Server Release:  11600000
    X Window Manager:  GNOME Shell
    Steam Runtime Version:  steam-runtime-release_2015-01-06
    
Video Card:
    Driver:  NVIDIA Corporation GeForce GTX 750 Ti/PCIe/SSE2


    Driver Version:  1.4 (2.1.2 NVIDIA 346.47)
    OpenGL Version: 1.4
    Desktop Color Depth: 24 bits per pixel
    Monitor Refresh Rate: 59 Hz
    VendorID:  0x10de
    DeviceID:  0x1380
    Number of Monitors:  2
    Number of Logical Video Cards:  1
    Primary Display Resolution:  1680 x 1050
    Desktop Resolution: 2960 x 1050
    Primary Display Size: 6.30" x 3.54"  (7.20" diag)
                                            16.0cm x 9.0cm  (18.3cm diag)
    Primary Bus: PCI Express 16x
    Primary VRAM Not Detected
    Supported MSAA Modes:  2x 4x 8x 16x 
    
Sound card:
    Audio device: Realtek ALC892
    
Memory:
    RAM:  16000 Mb
    
Miscellaneous:
    UI Language:  English
    LANG:  en_US.UTF-8
    Microphone:  Not set
    Total Hard Disk Space Available:  218281 Mb
    Largest Free Hard Disk Block:  184031 Mb
    
Installed software:
    
Recent Failure Reports:
    Mon Mar 23 21:15:57 2015 GMT: file ''/tmp/dumps/crash_20150323171411_2.dmp'', upload yes: ''CrashID=bp-34d0630b-cc6e-4e4f-8b0c-7b7552150323''
    
How can I link Steam's version of OpenGL with my graphics cards? Or is this not my real problem?
Thank you.

---

### Post by sffvba[e0rt on 2015-03-24
I checked my setup and my steam shows the same version of opengl as my nvidia drivers shows.  I see you are running the latest available nvidia driver... did you install it via PPA?  Perhaps you can see what happens if you use one that is available by default from the repo's?

---

### Post by efflandt on 2015-03-24
Not sure why yours shows that GL version. I am using xorg-edgers ppa for same video chip in 14.04 and mine shows:```
Operating System Version: 
    Ubuntu 14.04.2 LTS (64 bit) 
    Kernel Name:  Linux 
    Kernel Version:  3.13.0-48-generic 
    X Server Vendor:  The X.Org Foundation 
    X Server Release:  11501000 
    X Window Manager:  Compiz 
    Steam Runtime Version:  steam-runtime-release_2015-01-06 
     
Video Card: 
    Driver:  NVIDIA Corporation GeForce GTX 750 Ti/PCIe/SSE2 
 
    Driver Version:  4.5.0 NVIDIA 346.47 
    OpenGL Version: 4.5 
    Desktop Color Depth: 24 bits per pixel 
    Monitor Refresh Rate: 60 Hz 
    VendorID:  0x10de 
    DeviceID:  0x1380 
    Number of Monitors:  1 
    Number of Logical Video Cards:  1 
    Primary Display Resolution:  1920 x 1080 
    Desktop Resolution: 1920 x 1080 
    Primary Display Size: 45.28" x 25.59"  (51.97" diag) 
                                            115.0cm x 65.0cm  (132.0cm diag) 
    Primary Bus: PCI Express 16x 
    Primary VRAM: 2048 MB 
    Supported MSAA Modes:  2x 4x 8x 16x
```My display is actually 32" not 52" and I assume yours is not actually 7.2". I just noticed that it does not detect your VRAM.

---

