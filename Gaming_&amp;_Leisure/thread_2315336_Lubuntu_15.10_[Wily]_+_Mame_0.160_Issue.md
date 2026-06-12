---
title: "Lubuntu 15.10 [Wily] + Mame 0.160 Issue"
date: 2016-02-27
forum: Gaming &amp; Leisure
---

### Post by cool.kc-2016 on 2016-02-27
Hello Lubuntu/Ubuntu/MAME community,

I'm trying to figure out why there is an error when I load the following in terminal:

```
mame
```

[B]libGL error: failed to create dri screen
libGL error: failed to load driver: i915[/B]

I tried to run "mame -debug" but was kicked back an error which I sent the report.

It will still load the MAME emulator but has a lag when I try to use it, so I have to F8/F9 frameskip or autoskip to play the games most the time. Before the recent updates in Lubuntu, it was working flawlessly without any adjustments.
[U][B]
lspci *shows the following:*[/B][/U]
00:02:0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
[B]_locate *i915*_[I][U] shows the following:
[/U][/I][/B]/usr/lib/i386-linux-gnu/dri/i915_dri.so

I had prior issues installing the MAME emulator and went through a series of things to install/fix which has all 3 times led to me getting to the issue I'm posting now without resolve. 
[U][B]
Here is the Youtube video I made of what I am using/how I fixed the prior:[/B][/U]
[https://www.youtube.com/watch?v=9txgLBJHIbw](https://www.youtube.com/watch?v=9txgLBJHIbw)

SYSTEM:
DELL DIMENSION 3000 [2048MB]
CPU = Intel Celeron(R) CPU 2.40GHz
KERNEL = 4.2.0-30-generic

If anyone can please assist, I would greatly appreciate!

---

### Post by MikeCyber on 2016-02-28
The GL error is related to your graphics driver. Can you run 3D games? Make sure to have the latest Intel driver installed. I use the proprietary Nvidia driver, but I guess you need Mesa.

---

### Post by cool.kc-2016 on 2016-02-28
MikeCyber,

Thanks for your help, here are some additional steps I've taken to further troubleshoot this desktop below. I'm only running ROM emulators like MAME which was a major tasking to setup. I'm not running any 3D games but have installed driconf from terminal [you can see in screenshot below running] to assist getting this working correctly. 

_**FYI: I noticed on this page:**_ [http://wiki.mamedev.org/index.php/FAQ:Performance](http://wiki.mamedev.org/index.php/FAQ:Performance)

There was a mention of Hyperthreading that can be used, which my CPU doesn't support at least from specs shown here [**[http://ark.intel.com/products/27107/Intel-Celeron-D-Processor-320-256K-Cache-2_40-GHz-533-MHz-FSB](http://ark.intel.com/products/27107/Intel-Celeron-D-Processor-320-256K-Cache-2_40-GHz-533-MHz-FSB)] **but when i tried the following in terminal:

```
 mame -mt 
```

_**This actually made the emulator work like it was before!**_ I'm pleased such actually helped out but I would like to still appreciate info/clues of what else to try. I don't have any type of xorg.conf file currently, and am still trying to figure out why it worked fine the first time I installed MAME. I did an update on Lubuntu, and am left with the following issue stated above still occurring. 

Tried to get the latest intel driver and had this happen:

```
**sudo apt-get install xserver-xorg-video-intel**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
**xserver-xorg-video-intel is already the newest version.**
xserver-xorg-video-intel set to manually installed.
The following package was automatically installed and is no longer required:
  libllvm3.6v5
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```
[U][B]
Few screenshots of applications I've used to help the process of troubleshooting to help resolve this issue better:[/B][/U]

[IMG]http://i66.tinypic.com/207oraf.png[/IMG]

[IMG]http://i65.tinypic.com/t89c7q.png[/IMG]

[IMG]http://i67.tinypic.com/2vvtba8.png[/IMG]

_**Other programs used also to give more indepth of what is happening/what's installed on my system:**_

```
[B]dpkg --get-selections | grep mesa
[/B]
libegl1-mesa:i386                install
libegl1-mesa-dev:i386                install
libgl1-mesa-dri:i386                install
libgl1-mesa-glx:i386                install
libglapi-mesa:i386                install
libglu1-mesa:i386                install
libosmesa6:i386                    install
libwayland-egl1-mesa:i386            install
mesa-utils                    install
mesa-vdpau-drivers:i386                install

```

```
[B]LIBGL_DEBUG=verbose glxgears
[/B]
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/i915_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/i915_dri.so
libGL error: failed to create dri screen
libGL error: failed to load driver: i915
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
379 frames in 5.0 seconds = 75.693 FPS
618 frames in 5.0 seconds = 123.481 FPS
621 frames in 5.0 seconds = 124.021 FPS
620 frames in 5.0 seconds = 123.817 FPS
^C

```

```
**inxi -Fxz**

System:    Host: lubuntucarecomplex-Dimension-3000 Kernel: 4.2.0-30-generic i686 (32 bit gcc: 5.2.1)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 15.10 wily
Machine:   System: Dell product: Dimension 3000
           Mobo: Dell model: 0N6381 Bios: Dell v: A03 date: 01/05/2006
CPU:       Single core Intel Celeron (-UP-) cache: 256 KB
           flags: (pae sse sse2 sse3) bmips: 4788 speed: 2394 MHz (max)
Graphics:  Card: Intel 82865G Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: X.Org 1.17.2 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x1024@60.02hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
           GLX Version: 3.0 Mesa 11.3.0-devel (git-aa3b85f 2016-02-28 wily-oibaf-ppa) Direct Rendering: Yes

```

```
[B]fglrxinfo
[/B]
libGL error: failed to create dri screen
libGL error: failed to load driver: i915
display: :0.0  screen: 0
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
OpenGL version string: 3.0 Mesa 11.3.0-devel (git-aa3b85f 2016-02-28 wily-oibaf-ppa)

```

```
[B]dpkg -s xserver-xorg-video-intel
[/B]
Package: xserver-xorg-video-intel
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 3213
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 2:2.99.917+git1602241932.d16728~gd~w
Provides: xorg-driver-video
Depends: libc6 (>= 2.17), libdrm-intel1 (>= 2.4.38), libdrm2 (>= 2.4.25), libpciaccess0 (>= 0.8.0+git20071002), libpixman-1-0 (>= 0.30.0), libudev1 (>= 183), libx11-6, libx11-xcb1, libxcb-dri2-0, libxcb-util1 (>= 0.4.0), libxcb1, libxv1, libxvmc1, xorg-video-abi-19, xserver-xorg-core (>= 2:1.16.99.901)
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family
 of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
 and i965 series chips.
 .
 This package also provides XvMC (XVideo Motion Compensation) drivers
 for i810/i815 and i9xx and newer chipsets.
 .
 This package is built from the X.org xf86-video-intel driver module.
Homepage: http://www.x.org/
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
```

**EDIT:** I've installed the following into my machine and got even more gfx working but still having that error when I load MAME..
Now my **[COLOR=#ff0000]text[/COLOR]** in terminal is different with **[COLOR=#ff0000]color[/COLOR]** on folders!
[IMG]http://i64.tinypic.com/24z9hjr.png[/IMG]

I tried this and couldn't get it the install.sh to compile,load the driver I needed:
[IMG]http://i67.tinypic.com/2ldvspf.png[/IMG]


**Any additional tips/thoughts/ideas?? All help is appreciated.. I'm trying out everything I can to figure out how to get this to operate.. Thanks!**

---

### Post by MikeCyber on 2016-02-29
Quickly looking through I saw:
OpenGL vendor string: VMware, Inc.

I don't think VMware supports accelerated 3D.- They say so as a joke, like Virtualbox etc., but in fact it's way to slow.

---

### Post by cool.kc-2016 on 2016-02-29
[B]All,

_Here's the solution I figured out and removed my error:_[/B]

```
**sudo apt-get remove libgl1-mesa-dri:i386**
```

Doing this showed some unmet dependencies [The clue I needed] and _**wouldn't let me uninstall this package without removing the ppa**_. I figured I'd start removing drivers to see what the issue was, it was the next step to troubleshoot this issue.
[U]
[Wine **MUST** be installed along with the oibaf PPA!] [/U]

_**I removed the following two ppa repositories:**_

**ppa:ubuntu-x-swat/x-updates** [I did this one in **LXDE Start Menu > Preferences > Additional Drivers > Other Software** **[TAB]**
**sudo ppa-purge ppa:oibaf/graphics-drivers **[Terminal]

```
_**The following packages will be DOWNGRADED:**_
  libdrm-amdgpu1 libdrm-dev libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 
  libdrm2 libegl1-mesa libegl1-mesa-dev libgbm1 libgl1-mesa-dri 
  libgl1-mesa-glx libglapi-mesa libosmesa6 libva-x11-1 libva1 libvdpau1 
  libvorbis0a libvorbisenc2 libvorbisfile3 libwayland-egl1-mesa 
  libxatracker2 mesa-utils mesa-vdpau-drivers xserver-xorg-video-ati 
  xserver-xorg-video-intel xserver-xorg-video-nouveau 
  xserver-xorg-video-radeon 
The following NEW packages will be installed:
  libllvm3.6v5{a} 
The following packages will be REMOVED:
  libllvm3.8{u} libomxil-bellagio-bin{u} libomxil-bellagio0{u} 
  vdpau-driver-all{u} 
The following packages are RECOMMENDED but will NOT be installed:
  i965-va-driver va-driver-all vdpau-va-driver 
0 packages upgraded, 1 newly installed, 27 downgraded, 4 to remove and 1 not upgraded.

```

```
**dpkg: warning: downgrading libgl1-mesa-dri:i386 from 11.3~git1602290730.07ed00~gd~w to 11.0.2-1ubuntu4**
Preparing to unpack .../libgl1-mesa-dri_11.0.2-1ubuntu4_i386.deb ...
Unpacking libgl1-mesa-dri:i386 (11.0.2-1ubuntu4) over (11.3~git1602290730.07ed00~gd~w) ...

```

Since Lubuntu 15.10 had some recent updates again regarding all the mesa driver packages, it was time to revert from the drivers I originally had working from those ppa repositories. 

I still kept the following packages above and added this one from the unmet dependencies shown in the remove prompt: ```
sudo apt-get install kde-runtime
``` [Leaving it installed since it system is working well now]

*I added "**sudo apt-get install pulseaudio**" to remove ALSA pcm errors I was having when it was the other ppa driver installed, just throwing that in extra*

All the other applications I had installed previously like mesa-utils, etc did downgrade to official ubuntu packages and now the issue is resolved!! 

```
**dpkg --get-selections | grep mesa**

libegl1-mesa:i386                install
libegl1-mesa-dev:i386                install
libgl1-mesa-dri:i386                install
libgl1-mesa-glx:i386                install
libglapi-mesa:i386                install
libglu1-mesa:i386                install
libosmesa6:i386                    install
libwayland-egl1-mesa:i386            install
mesa-utils                    install
mesa-vdpau-drivers:i386                install

```

```
mame -mt -video opengl -rs -speed 1.00
```
**Average speed: 68.03% (185 seconds)**

Now MAME is working correctly with the -Video OpenGL option [No more -Video Soft needed!] Errors gone!

[IMG]http://i66.tinypic.com/293cayp.png[/IMG]

[IMG]http://i67.tinypic.com/2hq5t2x.png[/IMG]

**FINAL EDIT: **

OK, so the issue **did** return after a reboot of the PC. Here is what I did as follows.. I backtraced and was able to duplicate the final desired effect of MAME 0.160 working perfect after I re-installed the oibaf PPA with apt-get update.
Then ran "Software Updater" to find the updates with the new software updating..

[IMG]http://i63.tinypic.com/2yxmz29.png[/IMG]

Then after the updates, ppa purged the oibaf repository and was able to pinpoint it was the intel driver from this PPA
I needed. Figuring this out, here is what I did to finally get the easy and final fix:

When back to the oibaf link here: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers/+packages](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers/+packages)

[IMG]http://i68.tinypic.com/mm4p5.png[/IMG]
[B]
Installed these two and now everything is _COMPLETE/WORKING!!_[/B]

[xserver-xorg-video-intel-dbg_2.99.917+git1602241932.d16728~gd~w_i386.deb]("https://launchpad.net/%7Eoibaf/+archive/ubuntu/graphics-drivers/+files/xserver-xorg-video-intel-dbg_2.99.917+git1602241932.d16728%7Egd%7Ew_i386.deb")          (2.6 MiB)     

[xserver-xorg-video-intel_2.99.917+git1602241932.d16728~gd~w_i386.deb]("https://launchpad.net/%7Eoibaf/+archive/ubuntu/graphics-drivers/+files/xserver-xorg-video-intel_2.99.917+git1602241932.d16728%7Egd%7Ew_i386.deb")          (1.6 MiB)     

**Hope this helps someone with MAME who tries to get it working, and runs into this issue running it installing/configuring from Terminal.**

---

