---
title: "X server not starting (with bumblebee)"
date: 2013-12-22
forum: Desktop Environments
---

### Post by geordan on 2013-12-22
I'm running Ubuntu 13.10 dual booted on an MSi GS70 laptop, using the nvidia-331 drivers from xorg-edgers.  It was running fine until a recent reboot, after which the X server refuses to start.

The behavior I'm seeing is: normal boot output (I have quiet and splash off), and then an attempt to start X, which fails.  It then leaves me at the X tty which no X server running.  I can alt-F1 to get back to the first tty.

Notably, I'm seeing in Xorg.0.conf and Xorg.failsafe.conf:

```

[   462.042] (EE) open /dev/dri/card0: No such file or directory
[   462.043] (EE) VESA(0): V_BIOS address 0xd00 out of range
[   462.043] (EE) Screen(s) found, but none have a usable configuration.

```

Before I started having this problem I did an aptitude safe-upgrade, which may have introduced some configuration changes.  Maybe the new xserver-xorg-video-intel driver from the xorg-edgers PPA is bad?
[B]
Things I have tried:
[/B]
[LIST]
[*]Reinstalling nvidia drivers and bumblebee with --purge
[*]Editing the BusID in xorg.conf.nvidia to match the output of lspci exactly (changing "01:00:0" to "01:00.0")
[*]Messing with update-alternatives --config x86_64-linux-gnu_gl_conf (currently set to its original setting of manual mode pointing at the non-nvidia on in /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf)
[/LIST]

I did have to mess with /etc/default/grub to add "nomodeset" and remove "quick splash" which would hang on startup when probing the video cards.  This was how it was before I was having problems, and for some reason I had to put it back.  That got me to the point where I could see log output during the boot process.

I notice there's no /etc/bumblebee/xorg.conf.intel; I don't remember if there never was one, or if one was removed during a package update.

Log files and other info below.

**Xorg.0.log:**
```

[   462.035] 
X.Org X Server 1.14.4.901 (1.14.5 RC 1)Release Date: 2013-11-21
[   462.035] X Protocol Version 11, Revision 0
[   462.035] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[   462.035] Current Operating System: Linux dot 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64
[   462.035] Kernel command line: BOOT_IMAGE=/vmlinuz-3.11.0-14-generic root=UUID=eaddec11-a1cb-417a-9c3b-e88cfefbf818 ro nomodeset
[   462.035] Build Date: 03 December 2013  05:02:27PM
[   462.035] xorg-server 2:1.14.4.901+git20131203+server-1.14-branch.c30db601-0ubuntu0sarvatt4 (For technical support please see http://www.ubuntu.com/support) 
[   462.035] Current version of pixman: 0.30.2
[   462.035]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   462.035] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   462.035] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 22 17:44:17 2013
[   462.035] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   462.035] (==) No Layout section.  Using the first Screen section.
[   462.035] (==) No screen section available. Using defaults.
[   462.035] (**) |-->Screen "Default Screen Section" (0)
[   462.035] (**) |   |-->Monitor "<default monitor>"
[   462.035] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   462.035] (==) Automatically adding devices
[   462.035] (==) Automatically enabling devices
[   462.035] (==) Automatically adding GPU devices
[   462.035] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   462.035]     Entry deleted from font path.
[   462.035] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   462.035]     Entry deleted from font path.
[   462.035] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   462.035]     Entry deleted from font path.
[   462.035] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   462.035]     Entry deleted from font path.
[   462.035] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   462.035]     Entry deleted from font path.
[   462.035] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   462.035] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   462.035] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   462.035] (II) Loader magic: 0x7fdc883e5d20
[   462.035] (II) Module ABI versions:
[   462.035]     X.Org ANSI C Emulation: 0.4
[   462.035]     X.Org Video Driver: 14.1
[   462.035]     X.Org XInput driver : 19.1
[   462.035]     X.Org Server Extension : 7.0
[   462.036] (--) PCI:*(0:0:2:0) 8086:0416:1462:10ee rev 6, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[   462.036] (--) PCI: (0:1:0:0) 10de:11e1:1462:10ee rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   462.036] (II) Open ACPI successful (/var/run/acpid.socket)
[   462.036] Initializing built-in extension Generic Event Extension
[   462.036] Initializing built-in extension SHAPE
[   462.036] Initializing built-in extension MIT-SHM
[   462.036] Initializing built-in extension XInputExtension
[   462.036] Initializing built-in extension XTEST
[   462.036] Initializing built-in extension BIG-REQUESTS
[   462.036] Initializing built-in extension SYNC
[   462.036] Initializing built-in extension XKEYBOARD
[   462.036] Initializing built-in extension XC-MISC
[   462.036] Initializing built-in extension SECURITY
[   462.036] Initializing built-in extension XINERAMA
[   462.036] Initializing built-in extension XFIXES
[   462.036] Initializing built-in extension RENDER
[   462.036] Initializing built-in extension RANDR
[   462.036] Initializing built-in extension COMPOSITE
[   462.036] Initializing built-in extension DAMAGE
[   462.036] Initializing built-in extension MIT-SCREEN-SAVER
[   462.036] Initializing built-in extension DOUBLE-BUFFER
[   462.036] Initializing built-in extension RECORD
[   462.036] Initializing built-in extension DPMS
[   462.036] Initializing built-in extension X-Resource
[   462.036] Initializing built-in extension XVideo
[   462.036] Initializing built-in extension XVideo-MotionCompensation
[   462.036] Initializing built-in extension SELinux
[   462.036] Initializing built-in extension XFree86-VidModeExtension
[   462.036] Initializing built-in extension XFree86-DGA
[   462.036] Initializing built-in extension XFree86-DRI
[   462.036] Initializing built-in extension DRI2
[   462.036] (II) "glx" will be loaded by default.
[   462.036] (WW) "xmir" is not to be loaded by default. Skipping.
[   462.036] (II) LoadModule: "dri2"
[   462.036] (II) Module "dri2" already built-in
[   462.036] (II) LoadModule: "glamoregl"
[   462.036] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   462.037] (II) Module glamoregl: vendor="X.Org Foundation"
[   462.037]     compiled for 1.14.3, module version = 0.5.1
[   462.037]     ABI class: X.Org ANSI C Emulation, version 0.4
[   462.037] (II) LoadModule: "glx"
[   462.037] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   462.037] (II) Module glx: vendor="X.Org Foundation"
[   462.037]     compiled for 1.14.4.901, module version = 1.0.0
[   462.037]     ABI class: X.Org Server Extension, version 7.0
[   462.037] (==) AIGLX enabled
[   462.037] Loading extension GLX
[   462.037] (==) Matched intel as autoconfigured driver 0
[   462.037] (==) Matched vesa as autoconfigured driver 1
[   462.037] (==) Matched modesetting as autoconfigured driver 2
[   462.037] (==) Matched fbdev as autoconfigured driver 3
[   462.037] (==) Assigned the driver to the xf86ConfigLayout
[   462.037] (II) LoadModule: "intel"
[   462.037] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   462.037] (II) Module intel: vendor="X.Org Foundation"
[   462.037]     compiled for 1.14.4.901, module version = 2.99.906
[   462.037]     Module class: X.Org Video Driver
[   462.037]     ABI class: X.Org Video Driver, version 14.1
[   462.037] (II) LoadModule: "vesa"
[   462.037] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   462.037] (II) Module vesa: vendor="X.Org Foundation"
[   462.037]     compiled for 1.14.1, module version = 2.3.2
[   462.037]     Module class: X.Org Video Driver
[   462.037]     ABI class: X.Org Video Driver, version 14.1
[   462.037] (II) LoadModule: "modesetting"
[   462.037] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   462.037] (II) Module modesetting: vendor="X.Org Foundation"
[   462.037]     compiled for 1.14.1, module version = 0.8.0
[   462.037]     Module class: X.Org Video Driver
[   462.037]     ABI class: X.Org Video Driver, version 14.1
[   462.037] (II) LoadModule: "fbdev"
[   462.038] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   462.038] (II) Module fbdev: vendor="X.Org Foundation"
[   462.038]     compiled for 1.14.1, module version = 0.4.3
[   462.038]     Module class: X.Org Video Driver
[   462.038]     ABI class: X.Org Video Driver, version 14.1
[   462.038] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   462.038] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[   462.038] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[   462.038] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[   462.038] (II) VESA: driver for VESA chipsets: vesa
[   462.038] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   462.038] (II) FBDEV: driver for framebuffer: fbdev
[   462.038] (++) using VT number 7


[   462.042] (WW) Falling back to old probe method for modesetting
[   462.042] (EE) open /dev/dri/card0: No such file or directory
[   462.042] (WW) Falling back to old probe method for fbdev
[   462.042] (II) Loading sub module "fbdevhw"
[   462.042] (II) LoadModule: "fbdevhw"
[   462.042] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   462.043] (II) Module fbdevhw: vendor="X.Org Foundation"
[   462.043]     compiled for 1.14.4.901, module version = 0.0.2
[   462.043]     ABI class: X.Org Video Driver, version 14.1
[   462.043] (II) Loading sub module "vbe"
[   462.043] (II) LoadModule: "vbe"
[   462.043] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   462.043] (II) Module vbe: vendor="X.Org Foundation"
[   462.043]     compiled for 1.14.4.901, module version = 1.1.0
[   462.043]     ABI class: X.Org Video Driver, version 14.1
[   462.043] (II) Loading sub module "int10"
[   462.043] (II) LoadModule: "int10"
[   462.043] (II) Loading /usr/lib/xorg/modules/libint10.so
[   462.043] (II) Module int10: vendor="X.Org Foundation"
[   462.043]     compiled for 1.14.4.901, module version = 1.0.0
[   462.043]     ABI class: X.Org Video Driver, version 14.1
[   462.043] (II) VESA(0): initializing int10
[   462.043] (EE) VESA(0): V_BIOS address 0xd00 out of range
[   462.043] (II) UnloadModule: "vesa"
[   462.043] (II) UnloadSubModule: "int10"
[   462.043] (II) Unloading int10
[   462.043] (II) UnloadSubModule: "vbe"
[   462.043] (II) Unloading vbe
[   462.043] (EE) Screen(s) found, but none have a usable configuration.
[   462.043] (EE) 
Fatal server error:
[   462.043] (EE) no screens found(EE) 
[   462.043] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   462.043] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   462.043] (EE) 
[   462.047] (EE) Server terminated with error (1). Closing log file.

```
**bumblebee.conf:**
```

# Configuration file for Bumblebee. Values should **not** be put between quotes


## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d


## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false




# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods


## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-331
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-331:/usr/lib32/nvidia-331
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-331/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia


## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

```

[B]xorg.conf.nvidia:
[/B]
```
Section "ServerLayout"
    Identifier  "Layout0"
    Option      "AutoAddDevices" "false"
    Option      "AutoAddGPU" "false"
EndSection


Section "Device"
    Identifier  "DiscreteNvidia"
    Driver      "nvidia"
    VendorName  "NVIDIA Corporation"


#   If the X server does not automatically detect your VGA device,
#   you can manually set it here.
#   To get the BusID prop, run `lspci | egrep 'VGA|3D'` and input the data
#   as you see in the commented example.
#   This Setting may be needed in some platforms with more than one
#   nvidia card, which may confuse the proprietary driver (e.g.,
#   trying to take ownership of the wrong device). Also needed on Ubuntu 13.04.
    BusID "PCI:01:00.0"


#   Setting ProbeAllGpus to false prevents the new proprietary driver
#   instance spawned to try to control the integrated graphics card,
#   which is already being managed outside bumblebee.
#   This option doesn't hurt and it is required on platforms running
#   more than one nvidia graphics card with the proprietary driver.
#   (E.g. Macbook Pro pre-2010 with nVidia 9400M + 9600M GT).
#   If this option is not set, the new Xorg may blacken the screen and
#   render it unusable (unless you have some way to run killall Xorg).
    Option "ProbeAllGpus" "false"


    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "UseDisplayDevice" "none"
EndSection

```

**lspci | egrep 'VGA|3D':**
```

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)

```
[B]
Installed nvidia/bumblebee/xserver package versions:[/B]
```

ii  bumblebee                                 3.2.1-4+xedgers~saucy1                                                amd64        NVIDIA Optimus support for Linux
ii  bumblebee-nvidia                          3.2.1-4+xedgers~saucy1                                                amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  nvidia-331                                331.20-0ubuntu1~xedgers~saucy1                                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-persistenced                       331.20-0ubuntu1~xedgers~saucy1                                        amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-settings-331                       331.20-0ubuntu1~xedgers~saucy1                                        amd64        Tool for configuring the NVIDIA graphics driver
ii  xserver-xorg                              1:7.7+1ubuntu6                                                        amd64        X.Org X server
ii  xserver-xorg-core                         2:1.14.4.901+git20131203+server-1.14-branch.c30db601-0ubuntu0sarvatt4 amd64        Xorg X server - core server
ii  xserver-xorg-dev                          2:1.14.4.901+git20131203+server-1.14-branch.c30db601-0ubuntu0sarvatt4 amd64        Xorg X server - development files
ii  xserver-xorg-glamoregl:amd64              0.5.1-0ubuntu4.2                                                      amd64        X.Org X server -- graphics acceleration module based on OpenGL
ii  xserver-xorg-input-all                    1:7.7+1ubuntu6                                                        amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                  1:2.7.3-0ubuntu3.1                                                    amd64        X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse                  1:1.7.2-3build1                                                       amd64        X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics              1.7.1-0ubuntu1                                                        amd64        Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse                1:12.9.0-0ubuntu4                                                     amd64        X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom                  1:0.20.0-0ubuntu1                                                     amd64        X.Org X server -- Wacom input driver
ii  xserver-xorg-video-ati                    1:7.2.99~git20130816.d0323622-0ubuntu0smartboyhw                      amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus                 1:1.5.2-0ubuntu2                                                      amd64        X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                  1:0.4.3-0ubuntu3                                                      amd64        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-intel                  2:2.99.906+git20131213.f350a136-0ubuntu0sarvatt                       amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64                 6.9.3-0ubuntu3                                                        amd64        X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                    1:1.6.2-0ubuntu2                                                      amd64        X.Org X server -- MGA display driver
ii  xserver-xorg-video-modesetting            0.8.0-0ubuntu1.1                                                      amd64        X.Org X server -- Generic modesetting driver
ii  xserver-xorg-video-neomagic               1:1.2.7-0ubuntu3                                                      amd64        X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-openchrome             1:0.3.1-0ubuntu2.1                                                    amd64        X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                    0.1.0-0ubuntu3.1                                                      amd64        X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128                   6.9.1-0ubuntu2                                                        amd64        X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                 1:7.2.99~git20130816.d0323622-0ubuntu0smartboyhw                      amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                     1:0.6.5-0ubuntu3.1                                                    amd64        X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage                 1:2.3.6-0ubuntu3                                                      amd64        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion          1:1.7.7-0ubuntu3                                                      amd64        X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                    1:0.10.7-0ubuntu4                                                     amd64        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                 1:0.9.6-0ubuntu3                                                      amd64        X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                   1:1.4.5-0ubuntu3                                                      amd64        X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                1:1.3.6-0ubuntu4                                                      amd64        X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa                   1:2.3.2-0ubuntu3                                                      amd64        X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                 1:13.0.1-0ubuntu2                                                     amd64        X.Org X server -- VMware display driver

```

---

### Post by geordan on 2013-12-23
Turns out, a BIOS update I did must have reset the boot mode to UEFI (instead of UEFI with CSM).  In syslog:

```
video: module verification failed: signature and/or required key missing - tainting kernel
```

Switching back to UEFI with CSM fixed everything.

---

