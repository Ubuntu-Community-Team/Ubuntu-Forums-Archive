---
title: "HDMI Monitor Screen Resolution poor quality"
date: 2015-07-13
forum: Desktop Environments
---

### Post by Jonners59 on 2015-07-13
I am opening a new thread to resolve this problem:

I have attached an HDMI monitor to my PC.  The picture quality is not crisp, it has a glare and can be uncomfortable to read.


```
sudo lspci -v -s 01:00.0
```

[HTML]01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device 362b
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at fb000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia[/HTML]

Running NVIDIA 352 [COLOR=#222222][FONT=Verdana][SIZE=2]Installed Drivers: 304.125, 331, 340.76, 346.72, 349.16, 352.21[/SIZE][/FONT][/COLOR] and X-Org X-Server


xUbuntu 15:04 3.19.0-22-generic

```
 sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```
[HTML]There are 3 choices for the alternative x86_64-linux-gnu_gl_conf (providing /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf).

  Selection    Path                                       Priority   Status
------------------------------------------------------------
* 0            /usr/lib/nvidia-352/ld.so.conf              8604      auto mode
  1            /usr/lib/nvidia-352-prime/ld.so.conf        8603      manual mode
  2            /usr/lib/nvidia-352/ld.so.conf              8604      manual mode
  3            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode

Press enter to keep the current choice
[*], or type selection number: [/HTML]

```
head /proc/meminfo
```
[HTML]MemTotal:       16414560 kB
MemFree:        13791812 kB
MemAvailable:   15377804 kB
Buffers:          151636 kB
Cached:          1605128 kB
SwapCached:            0 kB
Active:          1280448 kB
Inactive:        1098680 kB
Active(anon):     623644 kB
Inactive(anon):    36780 kB[/HTML]

```
head /proc/cpuinfo
```
[HTML]processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
stepping    : 7
microcode    : 0x14
cpu MHz        : 1599.984
cache size    : 6144 KB
physical id    : 0[/HTML]

```
sudo dmidecode -t 2
```
[HTML]# dmidecode 2.12
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: P8P67-M PRO
    Version: Rev X.0X
    Serial Number: MT7014018601056
    Asset Tag: To be filled by O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To be filled by O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0[/HTML]

---

### Post by QDR06VV9 on 2015-07-13
I open myself up for a lot of debate here but I had similar results with a Vizio monitor.
I had on hand a thin middle of the road HDMI cable that I was using for my Laptop with Intel Graphics 3000 up.
But when I used that cable for my Box Tower the quality was about what you are describing now.
My Specs on the tower
```
inxi -b
System:    Host: mate-Aspire-M3300 Kernel: 4.0.6-040006-lowlatency x86_64 (64 bit) Desktop: N/A Distro: Ubuntu 14.04 trusty
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M Bios: American Megatrends version: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) clocked at 2600.00 MHz 
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GT 520/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 349.16
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller driver: sky2 
Drives:    HDD Total Size: 2508.6GB (3.8% used)
Info:      Processes: 233 Uptime: 7:13 Memory: 1409.5/5967.1MB Client: Shell (bash) inxi: 1.9.17 

```
After about 2 months I broke down and bought a nicer **High Speed HDMI Cable,** Well to my surprise it was worth the money for me.
[http://www.hdmi.org/consumer/finding_right_cable.aspx](http://www.hdmi.org/consumer/finding_right_cable.aspx)
This is where the debate comes in! But having witnessed the difference I am satisfied!
Oh quick note I also was able to change the resolution to 1920 x 1080 on both monitors going.
Kind Regards!

---

### Post by Jonners59 on 2015-07-14
> **runrickus said:**
> I open myself up for a lot of debate here but I had similar results with a Vizio monitor.
I had on hand a thin middle of the road HDMI cable that I was using for my Laptop with Intel Graphics 3000 up.
But when I used that cable for my Box Tower the quality was about what you are describing now.
My Specs on the tower
```
inxi -b
System:    Host: mate-Aspire-M3300 Kernel: 4.0.6-040006-lowlatency x86_64 (64 bit) Desktop: N/A Distro: Ubuntu 14.04 trusty
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M Bios: American Megatrends version: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) clocked at 2600.00 MHz 
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GT 520/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 349.16
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller driver: sky2 
Drives:    HDD Total Size: 2508.6GB (3.8% used)
Info:      Processes: 233 Uptime: 7:13 Memory: 1409.5/5967.1MB Client: Shell (bash) inxi: 1.9.17 

```
After about 2 months I broke down and bought a nicer **High Speed HDMI Cable,** Well to my surprise it was worth the money for me.
[http://www.hdmi.org/consumer/finding_right_cable.aspx](http://www.hdmi.org/consumer/finding_right_cable.aspx)
This is where the debate comes in! But having witnessed the difference I am satisfied!
Oh quick note I also was able to change the resolution to 1920 x 1080 on both monitors going.
Kind Regards!

Thanks for that I will try that out....  just need to find a cable.
Interestingly, before I bought this monitor I used 2 x 19".  One of those was fine the other displayed similar symptoms.  Could this be the reason why????

---

### Post by Jonners59 on 2015-07-15
OK, so I borrowed a cable from my local golf club...  It is slightly better, but not as crisp as I would have liked or expected.  It still has that sort of blotchy characters with a gloss, mostly visible on characters.

A step in the right direction.  Any other ideas, please?

---

### Post by QDR06VV9 on 2015-07-15
Maybe you have already, But the adjustments on your monitor?
It Needs to be a **High Speed HDMI Cable **to really notice the difference though.
> **High Speed HDMI Cable**
                 The High Speed HDMI cable is designed and tested to handle video resolutions                 of 1080p and beyond, including advanced display technologies such as 4K,                 3D, and Deep Color. If you are using any of these technologies, or if                 you are connecting your 1080p display to a 1080p content source, such                 as a Blu-ray Disc player, this is the recommended cable.
If your text is not sharp enough change to Subpixel Smoothing(LCDs) or play around to your liking.
Regards

---

### Post by Jonners59 on 2015-07-16
Just had a tinker with the Nvidia settings, the standard ones made no difference.  So i adjusted the Gamma, Brightness and contracts.  I managed to reduce the glare, but the characters are still not crisp and it is still possible to see the blotchiness, I think these settings just hide as best the issues.  Next it is the cable!

---

### Post by Jonners59 on 2015-08-03
No, cables make no difference at all.

I think this is a driver/settings issue.  Can anyone help me please.

---

