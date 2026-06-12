---
title: "Jaunty crashes after using an external screen"
date: 2009-07-31
forum: Desktop Environments
---

### Post by joopie18 on 2009-07-31
Hi everyone,
 
I'm in trouble here. I run the Jackalope and yesterdag I used an external screen (a huge one, actually a television). It worked fine, but the display settings where not what they were supposed to be on my laptop. I could, nevertheless play an entire DVD on my television (using my laptop of course). 
 
But here's the issue: whilst I was playing with the display settings, my entire display crashed. It is not an hardware issue (I run a dual boot, and :confused: the W$ does the job perfectly *frustration*)..
 
I tried xfix, does not work.
I tried to mannually reconfigure Xorg
I tried working adding a vga=790 setting to the /boot/grub/menu.lst in recovery mode
I pushed every button I know of
 
All this with no result, I can only get in recovery mode!
 
What might be of relevance is the fact that my loading screen (you know, that thing you get before you can login), looks unblemished, but my login is all messed up...
 
Any help would be really really appreciated. I'm stuck on this, and its my primary workstation..
 
greetings from the other side
walter

---

### Post by Dave_Connor on 2009-07-31
Have you tried disabling graphical boot with editing /boot/grub/menu.lst with removing "quite" and "splash" from your current kernel version. This should give you some insight if something is crashing upon boot.

---

### Post by joopie18 on 2009-07-31
Thanks for the idea.
I removed *quiet *and *splash *in the Grub edit option of the kernel and the error is exactly the same.
Any other ideas?
 
Gr
W

---

### Post by Dave_Connor on 2009-07-31
Have you tried disconnecting your TV and then booting to see if that might be the error ?

---

### Post by joopie18 on 2009-07-31
Yes, I have tried a series of about 20 different boots (both with and without pluggin the tele/external screen) to ensure I was not missing something. The tv has an option to choose the resolution, but I have not touched that until after the crashes...  
 
I personally think the display dialogue crashed as it reported some or other error before it asked me to login again. I changed the settings succesfully for several times and logging in every time without a problem before the crash. 
 
Gr
W

---

### Post by joopie18 on 2009-07-31
bump
not getting there...
comm'on guys, don't make me work on a silly W$ desktop...

---

### Post by Dave_Connor on 2009-07-31
Is it possible for you to post the error that your system is reporting back ?

---

### Post by joopie18 on 2009-07-31
I'm afraid that's not possible. Unless anyone can clearly explain whether there is a log file that logs things even before one logs in (unintended pun). I can probably get a hold of such a file if I can get there through recovery mode (using pico or nano)..
 
Help is really welcome as it might also consist of a bug in Jaunty..
 
Gr
W

---

### Post by joopie18 on 2009-07-31
bump

---

### Post by Dave_Connor on 2009-07-31
There is /var/log/Xorg.0.log can you post a copy of it ?

---

### Post by joopie18 on 2009-08-01
Hi everyone,
 
Here is the Xorg.0.log file. Help is really appreciated as I cannot use my system at present... 
 
Should I go for a but report?
 
Is it an option to simply reinstall Xorg in recovery mode? What would be the best way to go about it (without dataloss of course).
 
Gr
W
 
ps: I can also post Xorg.0.log.old as well as Xorg.failsafe and Xorg.failsafe.old
 
[FONT=Courier New][SIZE=1]X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
     to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
     (++) from command line, (!!) notice, (II) informational,
     (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 31 23:13:23 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
     Entry deleted from font path.
(==) FontPath set to:
     /usr/share/fonts/X11/misc,
     /usr/share/fonts/X11/100dpi/:unscaled,
     /usr/share/fonts/X11/75dpi/:unscaled,
     /usr/share/fonts/X11/Type1,
     /usr/share/fonts/X11/100dpi,
     /usr/share/fonts/X11/75dpi,
     /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
     built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
     If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
     X.Org ANSI C Emulation: 0.4
     X.Org Video Driver: 5.0
     X.Org XInput driver : 4.0
     X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xd8100000/524288, 0xc0000000/268435456, 0xd8200000/262144, I/O @ 0x00001800/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
     [0] -1     0    0xffffffff - 0xffffffff (0x1) MX[B]
     [1] -1     0    0x000f0000 - 0x000fffff (0x10000) MX[B]
     [2] -1     0    0x000c0000 - 0x000effff (0x30000) MX[B]
     [3] -1     0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
     [4] -1     0    0x0000ffff - 0x0000ffff (0x1) IX[B]
     [5] -1     0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
     compiled for 1.6.0, module version = 1.0.0
     Module class: X.Org Server Extension
     ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
     compiled for 1.6.0, module version = 1.0.0
     Module class: X.Org Server Extension
     ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
     compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
     compiled for 1.6.0, module version = 1.13.0
     Module class: X.Org Server Extension
     ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
     compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
     compiled for 1.4.99.906, module version = 8.60.40
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
     compiled for 1.6.0, module version = 1.0.0
     ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
     compiled for 1.6.0, module version = 2.6.3
     Module class: X.Org Video Driver
     ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
     i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
     E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
     965GM, 965GME/GLE, G33, Q35, Q33,
     Mobile Intel® GM45 Express Chipset,
     Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
     [0] -1     0    0xffffffff - 0xffffffff (0x1) MX[B]
     [1] -1     0    0x000f0000 - 0x000fffff (0x10000) MX[B]
     [2] -1     0    0x000c0000 - 0x000effff (0x30000) MX[B]
     [3] -1     0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
     [4] -1     0    0x0000ffff - 0x0000ffff (0x1) IX[B]
     [5] -1     0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
     [0] -1     0    0xffffffff - 0xffffffff (0x1) MX[B]
     [1] -1     0    0x000f0000 - 0x000fffff (0x10000) MX[B]
     [2] -1     0    0x000c0000 - 0x000effff (0x30000) MX[B]
     [3] -1     0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
     [4] 0 0    0x000a0000 - 0x000affff (0x10000) MS[B]
     [5] 0 0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
     [6] 0 0    0x000b8000 - 0x000bffff (0x8000) MS[B]
     [7] -1     0    0x0000ffff - 0x0000ffff (0x1) IX[B]
     [/SIZE][/FONT][FONT=Courier New][SIZE=1][8] -1     0    0x00000000 - 0x00000000 (0x1) IX[B]
     [9] 0 0    0x000003b0 - 0x000003bb (0xc) IS[B]
     [10] 0     0    0x000003c0 - 0x000003df (0x20) IS[B]
[/SIZE][/FONT][FONT=Courier New][SIZE=1](II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
     compiled for 1.6.0, module version = 0.1.0
     ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Creating default Display subsection in Screen section
     "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xD8100000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SEC", prod id 13125
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): Output TV has no monitor section
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): EDID vendor "SEC", prod id 13125
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
     compiled for 1.6.0, module version = 1.0.0
     ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
     compiled for 1.6.0, module version = 2.4.0
     ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
     [0] -1     0    0xffffffff - 0xffffffff (0x1) MX[B]
     [1] -1     0    0x000f0000 - 0x000fffff (0x10000) MX[B]
     [2] -1     0    0x000c0000 - 0x000effff (0x30000) MX[B]
     [3] -1     0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
     [4] 0 0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
     [5] 0 0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
     [6] 0 0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
     [7] -1     0    0x0000ffff - 0x0000ffff (0x1) IX[B]
     [/SIZE][/FONT][FONT=Courier New][SIZE=1][8] -1     0    0x00000000 - 0x00000000 (0x1) IX[B]
     [9] 0 0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
     [10] 0     0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
[/SIZE][/FONT][FONT=Courier New][SIZE=1](II) intel(0): Kernel reported 238592 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 954364 kB available
(WW) intel(0): DRI2 requires UXA
(EE) intel(0): [dri] I830CheckDRIAvailable failed because of a version mismatch.
[dri] libDRI version is 5.0.0 but version 5.4.x is needed.
[dri] Disabling DRI.
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): adjusting plane->pipe mappings to allow for framebuffer compression
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000003fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000003fe21000 physical
)
(II) intel(0): 0x0062b000-0x0072afff: fake bufmgr (1024 kB)
(II) intel(0): 0x0072b000-0x0072bfff: overlay registers (4 kB, 0x000000003ff2b000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (16384 kB)
(II) intel(0): 0x02000000-0x03dfffff: exa offscreen (30720 kB)
(II) intel(0): 0x10000000:            end of aperture
(WW) intel(0): PRB0_CTL (0x0001f001) indicates ring buffer enabled
(WW) intel(0): Existing errors found in hardware state.
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Failed
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
 [/SIZE][/FONT]

---

### Post by joopie18 on 2009-08-01
I found that I forgot to tell you some info that might be relevant. The reason I was playing around with the display settings (that were once again limited to a certain number of resolutions) was that I had two black bars on the sides (L&R) of my laptop monitor. After several attempts to reboot, I apt-got fglrx-kernel-source <none> 2:8.600-0ubuntu2 as to try another driver. Should I purge that driver?
 
Gr
W, still in trouble..

---

### Post by joopie18 on 2009-08-01
I removed (--purge of course) the fglrx-kernel-source driver and did xfix again. It worked! I could login and once logged in I could change the resolution back to normal. Thanks @Dave_conner anyway!
 
Gr
W

---

### Post by Dave_Connor on 2009-08-01
Your welcome for help with fixing your issue.

---

