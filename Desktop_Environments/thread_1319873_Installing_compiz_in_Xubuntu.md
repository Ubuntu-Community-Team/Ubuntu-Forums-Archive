---
title: "Installing compiz in Xubuntu"
date: 2009-11-08
forum: Desktop Environments
---

### Post by dustygoblin on 2009-11-08
I have been trying to install compiz onto my Xubuntu but am having a few issues.

I found a post on these forums that said to install the compiz packages from the package manager and then enter ALT+CTRL+F2 and type in ```
compiz --replace
``` to get it working, but when i enter that command i get this 

```
ryan@xubuntu-laptop:~$ compiz --replace 
No protocol specified 
xprop:  unable to open display ':0.0' 
Checking for Xgl: No protocol specified 
xvinfo:  Unable to open display :0.0 
not present.  
No protocol specified 
xset:  unable to open display ":0.0" 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log  
Detected PCI ID for VGA:  
Checking for texture_from_pixmap: not present.  
Trying again with indirect rendering: 
Checking for texture_from_pixmap: not present.  
SKIP_CHECKS is yes, so continuing despite problems. 
Checking for Software Rasterizer: Not present.  
Checking for nVidia: No protocol specified 
xdpyinfo:  unable to open display ":0.0". 
not present.  
Checking for FBConfig: No protocol specified 
Error: unable to open display :0.0 
not present.  
SKIP_CHECKS is yes, so continuing despite problems. 
Checking for Xgl: No protocol specified 
xvinfo:  Unable to open display :0.0 
not present.  
No protocol specified 
/usr/bin/compiz.real (core) - Fatal: Couldn't open display :0.0 
No protocol specified 
xterm Xt error: Can't open display: :0.0
```lspci -v outputs

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 011d
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 011d
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 011d
    Flags: bus master, fast devsel, latency 0
    Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
```


"glxinfo | grep direct" outputs
```
direct rendering: Yes
```


I had it working perfectly with no issues when i had Ubuntu installed on the laptop.

If anyone could help me out that would be great.

---

