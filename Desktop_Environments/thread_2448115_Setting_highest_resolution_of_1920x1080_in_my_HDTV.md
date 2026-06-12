---
title: "Setting highest resolution of 1920x1080 in my HDTV does not fill screen in 18.04 LTS"
date: 2020-08-02
forum: Desktop Environments
---

### Post by gsumaniitk2 on 2020-08-02
I have a *Ubuntu 18.04 LTS* desktop with *Intel integrated graphics (Ivybridge)* which I have connected to my Android TV using a VGA to HDMI adaptor (VGA from desktop to HDMI in TV). Ubuntu is unable to detect the highest resolution (1920x1080) automatically and these are the default modes listed by **xrandr**.
```

$ xrandr -q
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00*
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

I have used *xrandr* to add the 1920x1080 mode and use it following the set of commands below

```

xrandr --newmode "1920x1080_60.00"  173.00 1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

xrandr --addmode VGA1 "1920x1080_60.00"

xrandr --output VGA1 --mode "1920x1080_60.00"

```

The arguments to the newmode are generated using **"cvt"** utility. While the resolution appears to be okay, the aspect ratio does not seem to be 16:9 and the desktop does not fill the whole display as shown in the link below -
[https://gitlab.freedesktop.org/mesa/mesa/-/issues/3350](https://gitlab.freedesktop.org/mesa/mesa/-/issues/3350)

I have tried changing the refresh rate to the specified values of the TV manufacturer but without any success. I have also tried the different fitting option (Full, Unscaled, Wide, 16:9 etc.) provided in the TV's picture setting menu, which also doesn't help. I am a complete novice but I doubt that somehow the physical screen size is not detected properly, however I am not sure about that. I couldn't find this kind of issue anywhere. I'll truly appreciate any help in this regard.

Many thanks.

Here are some of the system info:

```

$ glxinfo -B
name of display: :1
display: :1  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: VMware, Inc. (0xffffffff)
    Device: llvmpipe (LLVM 10.0.0, 128 bits) (0xffffffff)
    Version: 20.1.4
    Accelerated: no
    Video memory: 3772MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 10.0.0, 128 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 20.1.4 - kisak-mesa PPA
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 3.1 Mesa 20.1.4 - kisak-mesa PPA
OpenGL shading language version string: 1.40
OpenGL context flags: (none)


OpenGL ES profile version string: OpenGL ES 3.1 Mesa 20.1.4 - kisak-mesa PPA
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10

```

```

$ inxi -Gxx
Graphics:  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics driver: i915 v: kernel bus ID: 00:02.0 
           chip ID: 8086:0152 
           Display: x11 server: X.Org 1.19.6 compositor: gnome-shell driver: intel resolution: 1920x1080~60Hz s-dpi: 96 
           OpenGL: renderer: llvmpipe (LLVM 10.0.0 128 bits) v: 3.3 Mesa 20.1.4 - kisak-mesa PPA compat-v: 3.1 
           direct render: Yes 

```

```

$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff

```

---

### Post by TheFu on 2020-08-02
**Found out this line of effort is completely unrelated.**

Look at the "VGA to HDMI adaptor" specs carefully.  When it provides EDID data to the GPU, does it send 1080p resolutions or not?

```
$ sudo get-edid | parse-edid
```
will show that information. If the adapter doesn't provide the data, I'd guess a better adapter is needed. 

I've used VGA-->HDMI and HDMI-->VGA converters. Always carefully purchased to ensure 1080p capable in their specs.  As long as I force the output from the GPU to be 1080p @ 60Hz, they work. 

But start by verifying the adapter supports 1080p.

---

### Post by gsumaniitk2 on 2020-08-02
Thanks for your reply. I had checked during purchase that it supported 1080p. Additionally I have used the same adaptor to connect my laptop to this TV and it works fine for Windows 10. Also, if it helps, I would also like to add that when I set the 1920x1080 resolution using xrandr, my TV shows a label 1080p on the top right corner.

Reading EDID info using the command actually fails. Here is the output of the command [B]sudo get-edid | parse-edid
[/B]```

This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful


    VBE version 300
    VBE string at 0x11100 "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"


VBE/DDC service about to be called
    Report DDC capabilities


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful


    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer


Reading next EDID block


VBE/DDC service about to be called
    Read EDID


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed


The EDID data should not be trusted as the VBE call failed
Error: output block unchanged

```

It appears that EDID is unable to fetch the data. Maybe that's why the output of the xrandr command does not show any info about the displaysize of the screen. It says 0x0. Is it because it fails to get the correct display size from EDID ?

---

### Post by Yellow Pasque on 2020-08-03
It looks like overscan. Double check that your TV doesn't have over/underscan settings. If it doesn't, you can try:
[https://wiki.archlinux.org/index.php/Xrandr#Correction_of_overscan_tv_resolutions_via_the_underscan_property](https://wiki.archlinux.org/index.php/Xrandr#Correction_of_overscan_tv_resolutions_via_the_underscan_property)

```
OpenGL: renderer: llvmpipe (LLVM 10.0.0 128 bits) v: 3.3 Mesa 20.1.4 - kisak-mesa PPA compat-v: 3.1 
```
It probably doesn't affect the resolution and you didn't complain about it, but you know ^this means there's a problem with the 3D acceleration, correct?

---

### Post by gsumaniitk2 on 2020-08-03
Thanks for your comment. Yes, there is a problem with the 3D acceleration. I am forced to use a custom xorg configuration file where DRI is set to 1, otherwise I get weird distorted graphics in ubuntu desktop. I guess setting DRI to "1" disables 3D acceleration, but I'm not sure about that. Although this graphics distortion is absent if I login to gnome flashback metacity.

I have checked in the TV's settings and tried all the different option as I mentioned in my original post, but it didn't help. I have seen most of the problem people face is related to cut off whereas in my case it's opposite. It's not filling the whole screen only in the horizontal direction. In the vertical direction it fits properly.

I'll try to take the suggestion from the link you have mentioned.

Many thanks.

---

### Post by TheFu on 2020-08-03
**Found out this line of effort is completely unrelated.**


The system is running inside a VM.  Not much we can do about 3D accel.  It isn't the VM that is controlling the output to the TV, it is the hostOS.

```
    Vendor: VMware, Inc. (0xffffffff)
    Device: llvmpipe (LLVM 10.0.0, 128 bits) (0xffffffff)
```

---

### Post by gsumaniitk2 on 2020-08-03
Sorry, I have a very little knowledge on the system and all these technical stuff. What is meant by the system is running inside a VM ? If it means a Virtual Machine, then I would like to share that I am not running any virtual machine. This desktop has only one OS installed Ubuntu 18.04. 

Please bear with my ignorance if it does not make any sense.


Many thanks.

---

### Post by TheFu on 2020-08-03
**Found out this line of effort is completely unrelated.**

VMware is a company that makes virtual machine software.  The fact that the GPU shown in the posted output above is from VMware is very telling. I cannot think of **any** other way to get VMware listed in the video output unless running inside a VM or using remote access from a VM system.  llvmpipe is the method that most VMs use to fake a GPU via software.  Those two items together scream "virtual machine."

I don't have any understanding for how both VMware and 
```
Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller 
```
can be shown on the same system without using a virtual machine.

I have a system with a built-in iGPU from intel.
**MY SYSTEM, not the OPs:**
```
$ inxi -Gxx
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0 chip-ID: 8086:0402
           Display Server: X.Org 1.19.6 drivers: (unloaded: fbdev,vesa) Resolution: 1920x1200@59.95hz
           GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A
```

Over an ssh -X (remote X11 connection) **MY SYSTEM, not the OPs:**
```
$ glxinfo -B
name of display: istar:10.0
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Error: couldn't find RGB GLX visual or fbconfig
```

When I run it from a direct login on the same machine **MY SYSTEM, not the OPs:**, 
```
$ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) Haswell Desktop  (0x402)
    Version: 18.0.5
    Accelerated: yes
    Video memory: 1536MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Desktop 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 18.0.5
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 3.0 Mesa 18.0.5
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 18.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
```

No VMware stuff.  There's something funky about DISPLAY=:1 on your system.  :0 is the main GPU. :1 is the 2nd GPU.  If a single card is used to control multiple outputs, normally a .0 or .1 or .2 are added to the DISPLAY variable.  DISPLAY=:0.0 or DISPLAY=:0.1 would be needed.  Ximera does something different. I don't know. [https://unix.stackexchange.com/questions/503806/what-are-x-server-display-and-screen](https://unix.stackexchange.com/questions/503806/what-are-x-server-display-and-screen) tries to explain the GPU - display - monitor relations.

It runs a few virtual machines, but that doesn't show up in the output, as you can see.

---

### Post by Yellow Pasque on 2020-08-03
llvmpipe does not mean it's a VM. While it was originally written by someone at VMWare (and is used in their VM's), llvmpipe is the default software rasterizer in Ubuntu (and I guess mesa in general). It outperforms the old "softpipe" implementation.

---

### Post by TheFu on 2020-08-03
**Found out this line of effort is completely unrelated.**

> **Yellow Pasque said:**
> llvmpipe does not mean it's a VM. While it was originally written by someone at VMWare (and is used in their VM's), llvmpipe is the default software rasterizer in Ubuntu (and I guess mesa in general). It outperforms the old "softpipe" implementation.

Interesting.  On a 20.04 box, but running inside a VM and accessed over the SPICE protocol using virt-viewer:
```
$ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: VMware, Inc. (0xffffffff)
    Device: llvmpipe (LLVM 10.0.0, 128 bits) (0xffffffff)
    Version: 20.0.8
    Accelerated: no
    Video memory: 1987MB
    Unified memory: no
```

Unfortunately, I don't have anything newer than 16.04 running on physical hardware and no way to directly access that 20.04 system except over a network connection.

gsumaniitk2, Should I attempt to clean up my posts above and remove the wild-goose-chase stuff?

---

### Post by deadflowr on 2020-08-03
> I am forced to use a custom xorg configuration file
Please post this.

---

### Post by gsumaniitk2 on 2020-08-03
TheFu, whatever you feel is right, please do. I have no problem. Many thanks.

---

### Post by gsumaniitk2 on 2020-08-04
I have a 20-intel.conf under /etc/X11/xorg.conf.d/ and this contains the following```
 
Section "Device"
         Identifier "Intel Graphics"
         Device "intel"
         Option "Tearfree" "true"
         Option "DRI"  "1"
         Option "Acceleration" "sna"
EndSection

```

I am using this workaround to solve the problem of the graphics which is posted here - [https://askubuntu.com/questions/1258012/distorted-graphics-in-ubuntu-18-04-with-intel-integrated-graphics/1259390?noredirect=1#comment2132024_1259390](https://askubuntu.com/questions/1258012/distorted-graphics-in-ubuntu-18-04-with-intel-integrated-graphics/1259390?noredirect=1#comment2132024_1259390)


Thanks.

---

### Post by deadflowr on 2020-08-04
Try switching 
```
Device "intel"
```
to
```
Driver "intel"
```

I think
```
Option "DRI"  "1"
```
might be useless as DRI1 as far as I know is unsupported these days.
Might try DRI2 instead.
```
Option "DRI"  "2"
```

---

### Post by gsumaniitk2 on 2020-08-04
> **deadflowr said:**
> Try switching 
```
Device "intel"
```
to
```
Driver "intel"
```


Sorry that was "Driver" only. My mistake, it was a typo.

> 
I think
```
Option "DRI"  "1"
```
might be useless as DRI1 as far as I know is unsupported these days.
Might try DRI2 instead.
```
Option "DRI"  "2"
```

There is a graphics issue if I change DRI to higher values. It's posted here [https://askubuntu.com/questions/1258012/distorted-graphics-in-ubuntu-18-04-with-intel-integrated-graphics/1259390?noredirect=1#comment2132024_1259390](https://askubuntu.com/questions/1258012/distorted-graphics-in-ubuntu-18-04-with-intel-integrated-graphics/1259390?noredirect=1#comment2132024_1259390)

Many thanks.

---

