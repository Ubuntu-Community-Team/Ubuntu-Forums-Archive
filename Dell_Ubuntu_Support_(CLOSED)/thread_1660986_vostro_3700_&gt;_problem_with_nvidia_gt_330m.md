---
title: "vostro 3700 &gt; problem with nvidia gt 330m"
date: 2011-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by redy1966 on 2011-01-06
i have a dell vostro 3700 with an intel g pu onboard and a nvidia gt 330m.

ubuntu 10.10 x64 works without problems, only the nvidia card makes troubles.
i can't activate the driver. i've tried all ways (driver installation from system>hardware, inst from synaptic & directly download from the nvidia site. also tried the nouveau driver) but with no success.

so, the hardware is well known under ubuntu:

```
lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)

```

any ideas?

greet
redy

---

### Post by lidex on 2011-01-06
Reference this post:
[http://ubuntuforums.org/showthread.php?t=1567861](http://ubuntuforums.org/showthread.php?t=1567861)

Can you post these outputs please:
```
sudo lshw -C display
cat /var/log/Xorg.0.log
cat /etc/X11/xorg.conf
```

---

### Post by redy1966 on 2011-01-07
okidoki,

a few words regarding the output:
i know my config is not very clean yet, because i tried some possibilities to activate the nvidia card.
i have 5 or 6 xorg.conf for different modes, the posted one is the current.

also i try to remove the intel module, but i doesn't work

```
lsmod | grep -i intel_a
intel_agp              32462  2 i915

cat /etc/modprobe.d/blacklist-nvidia.conf 
# blacklist fuer nvidia treiber
blacklist agpgart-intel
blacklist agpgart
blacklist intel_agp

``````
sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GT216 [GeForce GT 330M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f9000000-f9ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fa000000-fa07ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fa400000-fa7fffff memory:b0000000-bfffffff ioport:f080(size=8)

``````
cat /var/log/Xorg.0.log
[148337.171] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[148337.171] X Protocol Version 11, Revision 0
[148337.171] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[148337.171] Current Operating System: Linux dellgurke 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[148337.171] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=fcdab5e4-eae0-4ed0-ad27-da9908ad314d ro quiet splash
[148337.171] Build Date: 16 September 2010  06:18:41PM
[148337.171] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[148337.171] Current version of pixman: 0.18.4
[148337.171]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[148337.171] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[148337.171] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  6 13:44:14 2011
[148337.182] (==) Using config file: "/etc/X11/xorg.conf"
[148337.182] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[148337.192] (==) ServerLayout "Layout0"
[148337.192] (**) |-->Screen "Screen0" (0)
[148337.192] (**) |   |-->Monitor "Monitor0"
[148337.192] (**) |   |-->Device "Device0"
[148337.192] (**) |-->Input Device "Keyboard0"
[148337.192] (**) |-->Input Device "Mouse0"
[148337.192] (==) Automatically adding devices
[148337.192] (==) Automatically enabling devices
[148337.193] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[148337.193]     Entry deleted from font path.
[148337.207] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[148337.207] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[148337.207] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[148337.207] (WW) Disabling Keyboard0
[148337.207] (WW) Disabling Mouse0
[148337.207] (II) Loader magic: 0x7d0200
[148337.207] (II) Module ABI versions:
[148337.207]     X.Org ANSI C Emulation: 0.4
[148337.207]     X.Org Video Driver: 8.0
[148337.207]     X.Org XInput driver : 11.0
[148337.207]     X.Org Server Extension : 4.0
[148337.209] (--) PCI:*(0:0:2:0) 8086:0046:1028:044f rev 24, Mem @ 0xfa400000/4194304, 0xb0000000/268435456, I/O @ 0x0000f080/8
[148337.209] (--) PCI: (0:1:0:0) 10de:0a29:1028:044f rev 162, Mem @ 0xf9000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[148337.209] (II) Open ACPI successful (/var/run/acpid.socket)
[148337.209] (II) LoadModule: "extmod"
[148337.218] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[148337.218] (II) Module extmod: vendor="X.Org Foundation"
[148337.218]     compiled for 1.9.0, module version = 1.0.0
[148337.218]     Module class: X.Org Server Extension
[148337.218]     ABI class: X.Org Server Extension, version 4.0
[148337.218] (II) Loading extension MIT-SCREEN-SAVER
[148337.218] (II) Loading extension XFree86-VidModeExtension
[148337.218] (II) Loading extension XFree86-DGA
[148337.218] (II) Loading extension DPMS
[148337.218] (II) Loading extension XVideo
[148337.218] (II) Loading extension XVideo-MotionCompensation
[148337.218] (II) Loading extension X-Resource
[148337.219] (II) LoadModule: "dbe"
[148337.219] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[148337.219] (II) Module dbe: vendor="X.Org Foundation"
[148337.219]     compiled for 1.9.0, module version = 1.0.0
[148337.219]     Module class: X.Org Server Extension
[148337.219]     ABI class: X.Org Server Extension, version 4.0
[148337.219] (II) Loading extension DOUBLE-BUFFER
[148337.219] (II) LoadModule: "glx"
[148337.219] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[148337.230] (II) Module glx: vendor="X.Org Foundation"
[148337.230]     compiled for 1.9.0, module version = 1.0.0
[148337.230]     ABI class: X.Org Server Extension, version 4.0
[148337.230] (==) AIGLX enabled
[148337.230] (II) Loading extension GLX
[148337.230] (II) LoadModule: "record"
[148337.231] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[148337.231] (II) Module record: vendor="X.Org Foundation"
[148337.231]     compiled for 1.9.0, module version = 1.13.0
[148337.231]     Module class: X.Org Server Extension
[148337.231]     ABI class: X.Org Server Extension, version 4.0
[148337.231] (II) Loading extension RECORD
[148337.231] (II) LoadModule: "dri"
[148337.231] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[148337.231] (II) Module dri: vendor="X.Org Foundation"
[148337.231]     compiled for 1.9.0, module version = 1.0.0
[148337.231]     ABI class: X.Org Server Extension, version 4.0
[148337.231] (II) Loading extension XFree86-DRI
[148337.231] (II) LoadModule: "dri2"
[148337.232] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[148337.232] (II) Module dri2: vendor="X.Org Foundation"
[148337.232]     compiled for 1.9.0, module version = 1.2.0
[148337.232]     ABI class: X.Org Server Extension, version 4.0
[148337.232] (II) Loading extension DRI2
[148337.232] (==) Matched intel as autoconfigured driver 0
[148337.232] (==) Matched vesa as autoconfigured driver 1
[148337.232] (==) Matched fbdev as autoconfigured driver 2
[148337.232] (==) Assigned the driver to the xf86ConfigLayout
[148337.232] (II) LoadModule: "intel"
[148337.232] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[148337.238] (II) Module intel: vendor="X.Org Foundation"
[148337.238]     compiled for 1.9.0, module version = 2.12.0
[148337.238]     Module class: X.Org Video Driver
[148337.238]     ABI class: X.Org Video Driver, version 8.0
[148337.238] (II) LoadModule: "vesa"
[148337.239] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[148337.239] (II) Module vesa: vendor="X.Org Foundation"
[148337.239]     compiled for 1.8.99.905, module version = 2.3.0
[148337.239]     Module class: X.Org Video Driver
[148337.239]     ABI class: X.Org Video Driver, version 8.0
[148337.239] (II) LoadModule: "fbdev"
[148337.239] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[148337.240] (II) Module fbdev: vendor="X.Org Foundation"
[148337.240]     compiled for 1.8.99.905, module version = 0.4.2
[148337.240]     ABI class: X.Org Video Driver, version 8.0
[148337.240] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[148337.240] (II) VESA: driver for VESA chipsets: vesa
[148337.240] (II) FBDEV: driver for framebuffer: fbdev
[148337.241] (--) using VT number 7

[148337.248] (WW) Falling back to old probe method for vesa
[148337.248] (WW) Falling back to old probe method for fbdev
[148337.248] (II) Loading sub module "fbdevhw"
[148337.248] (II) LoadModule: "fbdevhw"
[148337.249] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[148337.249] (II) Module fbdevhw: vendor="X.Org Foundation"
[148337.249]     compiled for 1.9.0, module version = 0.0.2
[148337.249]     ABI class: X.Org Video Driver, version 8.0
[148337.367] drmOpenDevice: node name is /dev/dri/card0
[148337.367] drmOpenDevice: open result is 9, (OK)
[148337.367] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[148337.367] drmOpenDevice: node name is /dev/dri/card0
[148337.367] drmOpenDevice: open result is 9, (OK)
[148337.367] drmOpenByBusid: drmOpenMinor returns 9
[148337.367] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[148337.367] drmOpenDevice: node name is /dev/dri/card1
[148337.367] drmOpenDevice: open result is 9, (OK)
[148337.367] drmOpenByBusid: drmOpenMinor returns 9
[148337.367] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[148337.367] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[148337.367] (==) intel(0): RGB weight 888
[148337.367] (==) intel(0): Default visual is TrueColor
[148337.367] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[148337.367] (--) intel(0): Chipset: "Arrandale"
[148337.367] (==) intel(0): video overlay key set to 0x101fe
[148337.384] (II) intel(0): Output VGA1 using monitor section Monitor0
[148337.384] (II) intel(0): Output LVDS1 has no monitor section
[148337.384] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[148337.394] (II) intel(0): Output HDMI1 has no monitor section
[148337.395] (II) intel(0): Output DP1 has no monitor section
[148337.411] (II) intel(0): EDID for output VGA1
[148337.411] (II) intel(0): EDID for output LVDS1
[148337.411] (II) intel(0): Manufacturer: AUO  Model: 129e  Serial#: 0
[148337.411] (II) intel(0): Year: 2009  Week: 1
[148337.411] (II) intel(0): EDID Version: 1.3
[148337.411] (II) intel(0): Digital Display Input
[148337.411] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[148337.412] (II) intel(0): Gamma: 2.20
[148337.412] (II) intel(0): No DPMS capabilities specified
[148337.412] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[148337.412] (II) intel(0): First detailed timing is preferred mode
[148337.412] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.325 greenY: 0.570
[148337.412] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[148337.412] (II) intel(0): Manufacturer's mask: 0
[148337.412] (II) intel(0): Supported detailed timing:
[148337.412] (II) intel(0): clock: 110.0 MHz   Image Size:  382 x 214 mm
[148337.412] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 2000 h_border: 0
[148337.412] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 912 v_border: 0
[148337.412] (II) intel(0): Supported detailed timing:
[148337.412] (II) intel(0): clock: 110.0 MHz   Image Size:  382 x 214 mm
[148337.412] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 2000 h_border: 0
[148337.412] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 912 v_border: 0
[148337.412] (II) intel(0):  0D41C&#65533;B173RW1
[148337.412] (II) intel(0): Unknown vendor-specific block 0
[148337.412] (II) intel(0): EDID (in hex):
[148337.412] (II) intel(0):     00ffffffffffff0006af9e1200000000
[148337.412] (II) intel(0):     01130103902615780ac4959e57539226
[148337.412] (II) intel(0):     0f505400000001010101010101010101
[148337.412] (II) intel(0):     010101010101f82a409061840c303020
[148337.412] (II) intel(0):     36007ed61000001af82a409061840c30
[148337.412] (II) intel(0):     302036007ed61000001a000000fe0030
[148337.412] (II) intel(0):     44343143804231373352573100000000
[148337.412] (II) intel(0):     00000000000000000002010a20200054
[148337.412] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[148337.412] (II) intel(0): Printing probed modes for output LVDS1
[148337.412] (II) intel(0): Modeline "1600x900"x60.3  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148337.412] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[148337.412] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[148337.412] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[148337.412] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[148337.412] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[148337.412] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[148337.412] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[148337.412] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[148337.421] (II) intel(0): EDID for output HDMI1
[148337.422] (II) intel(0): EDID for output DP1
[148337.422] (II) intel(0): Output VGA1 disconnected
[148337.422] (II) intel(0): Output LVDS1 connected
[148337.422] (II) intel(0): Output HDMI1 disconnected
[148337.422] (II) intel(0): Output DP1 disconnected
[148337.422] (II) intel(0): Using user preference for initial modes
[148337.422] (II) intel(0): Output LVDS1 using initial mode 1600x900
[148337.422] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[148337.422] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[148337.422] (==) intel(0): DPI set to (96, 96)
[148337.422] (II) Loading sub module "fb"
[148337.422] (II) LoadModule: "fb"
[148337.423] (II) Loading /usr/lib/xorg/modules/libfb.so
[148337.436] (II) Module fb: vendor="X.Org Foundation"
[148337.436]     compiled for 1.9.0, module version = 1.0.0
[148337.436]     ABI class: X.Org ANSI C Emulation, version 0.4
[148337.436] (II) UnloadModule: "vesa"
[148337.436] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[148337.436] (II) UnloadModule: "fbdev"
[148337.436] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[148337.436] (II) UnloadModule: "fbdevhw"
[148337.436] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[148337.436] (==) Depth 24 pixmap format is 32 bpp
[148337.436] (II) intel(0): [DRI2] Setup complete
[148337.436] (II) intel(0): [DRI2]   DRI driver: i965
[148337.436] (**) intel(0): Tiling enabled
[148337.436] (**) intel(0): SwapBuffers wait enabled
[148337.436] (==) intel(0): VideoRam: 262144 KB
[148337.436] (II) intel(0): Allocated new frame buffer 1600x900 stride 6656, tiled
[148337.447] (II) UXA(0): Driver registered support for the following operations:
[148337.447] (II)         solid
[148337.447] (II)         copy
[148337.447] (II)         composite (RENDER acceleration)
[148337.447] (II)         put_image
[148337.447] (II)         get_image
[148337.448] (==) intel(0): Backing store disabled
[148337.448] (==) intel(0): Silken mouse enabled
[148337.448] (II) intel(0): Initializing HW Cursor
[148337.492] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[148337.494] (**) intel(0): DPMS enabled
[148337.494] (==) intel(0): Intel XvMC decoder enabled
[148337.494] (II) intel(0): Set up textured video
[148337.494] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[148337.494] (II) intel(0): direct rendering: DRI2 Enabled
[148337.494] (--) RandR disabled
[148337.494] (II) Initializing built-in extension Generic Event Extension
[148337.494] (II) Initializing built-in extension SHAPE
[148337.494] (II) Initializing built-in extension MIT-SHM
[148337.494] (II) Initializing built-in extension XInputExtension
[148337.494] (II) Initializing built-in extension XTEST
[148337.494] (II) Initializing built-in extension BIG-REQUESTS
[148337.494] (II) Initializing built-in extension SYNC
[148337.494] (II) Initializing built-in extension XKEYBOARD
[148337.494] (II) Initializing built-in extension XC-MISC
[148337.494] (II) Initializing built-in extension SECURITY
[148337.494] (II) Initializing built-in extension XINERAMA
[148337.494] (II) Initializing built-in extension XFIXES
[148337.494] (II) Initializing built-in extension RENDER
[148337.494] (II) Initializing built-in extension RANDR
[148337.494] (II) Initializing built-in extension COMPOSITE
[148337.494] (II) Initializing built-in extension DAMAGE
[148337.494] (II) Initializing built-in extension GESTURE
[148337.505] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[148337.505] (II) AIGLX: enabled GLX_INTEL_swap_event
[148337.505] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[148337.505] (II) AIGLX: enabled GLX_SGI_make_current_read
[148337.505] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[148337.505] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[148337.505] (II) GLX: Initialized DRI2 GL provider for screen 0
[148337.505] (II) intel(0): Setting screen physical size to 423 x 238
[148337.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[148337.613] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[148337.613] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[148337.613] (II) LoadModule: "evdev"
[148337.613] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[148337.613] (II) Module evdev: vendor="X.Org Foundation"
[148337.613]     compiled for 1.9.0, module version = 2.3.2
[148337.613]     Module class: X.Org XInput Driver
[148337.613]     ABI class: X.Org XInput driver, version 11.0
[148337.613] (**) Power Button: always reports core events
[148337.613] (**) Power Button: Device: "/dev/input/event3"
[148337.671] (II) Power Button: Found keys
[148337.671] (II) Power Button: Configuring as keyboard
[148337.671] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[148337.671] (**) Option "xkb_rules" "evdev"
[148337.671] (**) Option "xkb_model" "evdev"
[148337.671] (**) Option "xkb_layout" "de"
[148337.674] (II) XKB: reuse xkmfile /var/lib/xkb/server-1B5353734E7854C1F2B0553E65A16986C9AAC402.xkm
[148337.676] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[148337.676] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[148337.676] (**) Video Bus: always reports core events
[148337.676] (**) Video Bus: Device: "/dev/input/event11"
[148337.753] (II) Video Bus: Found keys
[148337.753] (II) Video Bus: Configuring as keyboard
[148337.753] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[148337.753] (**) Option "xkb_rules" "evdev"
[148337.753] (**) Option "xkb_model" "evdev"
[148337.753] (**) Option "xkb_layout" "de"
[148337.754] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[148337.755] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[148337.755] (**) Video Bus: always reports core events
[148337.755] (**) Video Bus: Device: "/dev/input/event10"
[148337.833] (II) Video Bus: Found keys
[148337.833] (II) Video Bus: Configuring as keyboard
[148337.833] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[148337.833] (**) Option "xkb_rules" "evdev"
[148337.833] (**) Option "xkb_model" "evdev"
[148337.833] (**) Option "xkb_layout" "de"
[148337.836] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[148337.836] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[148337.836] (**) Power Button: always reports core events
[148337.836] (**) Power Button: Device: "/dev/input/event0"
[148337.913] (II) Power Button: Found keys
[148337.913] (II) Power Button: Configuring as keyboard
[148337.913] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[148337.913] (**) Option "xkb_rules" "evdev"
[148337.913] (**) Option "xkb_model" "evdev"
[148337.913] (**) Option "xkb_layout" "de"
[148337.914] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[148337.914] (II) No input driver/identifier specified (ignoring)
[148337.914] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[148337.914] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[148337.914] (**) Sleep Button: always reports core events
[148337.914] (**) Sleep Button: Device: "/dev/input/event2"
[148338.033] (II) Sleep Button: Found keys
[148338.033] (II) Sleep Button: Configuring as keyboard
[148338.033] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[148338.033] (**) Option "xkb_rules" "evdev"
[148338.033] (**) Option "xkb_model" "evdev"
[148338.033] (**) Option "xkb_layout" "de"
[148338.037] (II) config/udev: Adding input device HID 413c:8161 (/dev/input/event6)
[148338.037] (**) HID 413c:8161: Applying InputClass "evdev keyboard catchall"
[148338.037] (**) HID 413c:8161: always reports core events
[148338.037] (**) HID 413c:8161: Device: "/dev/input/event6"
[148338.113] (II) HID 413c:8161: Found keys
[148338.113] (II) HID 413c:8161: Configuring as keyboard
[148338.113] (II) XINPUT: Adding extended input device "HID 413c:8161" (type: KEYBOARD)
[148338.113] (**) Option "xkb_rules" "evdev"
[148338.113] (**) Option "xkb_model" "evdev"
[148338.113] (**) Option "xkb_layout" "de"
[148338.115] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
[148338.115] (II) No input driver/identifier specified (ignoring)
[148338.115] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event13)
[148338.115] (II) No input driver/identifier specified (ignoring)
[148338.117] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event5)
[148338.117] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[148338.117] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[148338.118] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event5"
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[148338.193] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[148338.194] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[148338.194] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[148338.194] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[148338.194] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[148338.194] (II) No input driver/identifier specified (ignoring)
[148338.195] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event7)
[148338.195] (**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
[148338.195] (**) Laptop_Integrated_Webcam_2M: always reports core events
[148338.195] (**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event7"
[148338.273] (II) Laptop_Integrated_Webcam_2M: Found keys
[148338.273] (II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
[148338.273] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
[148338.273] (**) Option "xkb_rules" "evdev"
[148338.273] (**) Option "xkb_model" "evdev"
[148338.273] (**) Option "xkb_layout" "de"
[148338.277] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[148338.277] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[148338.277] (**) AT Translated Set 2 keyboard: always reports core events
[148338.277] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[148338.353] (II) AT Translated Set 2 keyboard: Found keys
[148338.353] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[148338.353] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[148338.353] (**) Option "xkb_rules" "evdev"
[148338.353] (**) Option "xkb_model" "evdev"
[148338.353] (**) Option "xkb_layout" "de"
[148338.354] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[148338.354] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[148338.354] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[148338.354] (II) LoadModule: "synaptics"
[148338.354] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[148338.354] (II) Module synaptics: vendor="X.Org Foundation"
[148338.354]     compiled for 1.9.0, module version = 1.2.2
[148338.354]     Module class: X.Org XInput Driver
[148338.354]     ABI class: X.Org XInput driver, version 11.0
[148338.354] (II) Synaptics touchpad driver version 1.2.2
[148338.355] (**) Option "Device" "/dev/input/event9"
[148338.793] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5650
[148338.793] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4710
[148338.793] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[148338.793] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[148338.793] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[148339.113] (--) SynPS/2 Synaptics TouchPad: touchpad found
[148339.113] (**) SynPS/2 Synaptics TouchPad: always reports core events
[148339.273] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[148339.273] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[148339.273] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[148339.273] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[148339.274] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[148339.513] (--) SynPS/2 Synaptics TouchPad: touchpad found
[148339.514] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[148339.514] (II) No input driver/identifier specified (ignoring)
[148339.518] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[148339.518] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[148339.518] (**) Dell WMI hotkeys: always reports core events
[148339.518] (**) Dell WMI hotkeys: Device: "/dev/input/event8"
[148339.593] (II) Dell WMI hotkeys: Found keys
[148339.593] (II) Dell WMI hotkeys: Configuring as keyboard
[148339.593] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[148339.593] (**) Option "xkb_rules" "evdev"
[148339.593] (**) Option "xkb_model" "evdev"
[148339.593] (**) Option "xkb_layout" "de"
[148340.225] (II) intel(0): EDID vendor "AUO", prod id 4766
[148340.226] (II) intel(0): Printing DDC gathered Modelines:
[148340.226] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148340.255] (II) intel(0): EDID vendor "AUO", prod id 4766
[148340.255] (II) intel(0): Printing DDC gathered Modelines:
[148340.255] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148340.283] (II) intel(0): EDID vendor "AUO", prod id 4766
[148340.283] (II) intel(0): Printing DDC gathered Modelines:
[148340.283] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148340.311] (II) intel(0): EDID vendor "AUO", prod id 4766
[148340.311] (II) intel(0): Printing DDC gathered Modelines:
[148340.311] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148346.655] (II) intel(0): EDID vendor "AUO", prod id 4766
[148346.655] (II) intel(0): Printing DDC gathered Modelines:
[148346.655] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148346.684] (II) intel(0): EDID vendor "AUO", prod id 4766
[148346.684] (II) intel(0): Printing DDC gathered Modelines:
[148346.684] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148346.712] (II) intel(0): EDID vendor "AUO", prod id 4766
[148346.712] (II) intel(0): Printing DDC gathered Modelines:
[148346.712] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148346.740] (II) intel(0): EDID vendor "AUO", prod id 4766
[148346.740] (II) intel(0): Printing DDC gathered Modelines:
[148346.740] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148347.293] (II) intel(0): EDID vendor "AUO", prod id 4766
[148347.293] (II) intel(0): Printing DDC gathered Modelines:
[148347.293] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148352.344] (II) intel(0): EDID vendor "AUO", prod id 4766
[148352.344] (II) intel(0): Printing DDC gathered Modelines:
[148352.344] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[150223.274] (II) intel(0): EDID vendor "AUO", prod id 4766
[150223.274] (II) intel(0): Printing DDC gathered Modelines:
[150223.274] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[154394.497] (II) intel(0): EDID vendor "AUO", prod id 4766
[154394.497] (II) intel(0): Printing DDC gathered Modelines:
[154394.497] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[156400.728] (II) intel(0): EDID vendor "AUO", prod id 4766
[156400.728] (II) intel(0): Printing DDC gathered Modelines:
[156400.728] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[163636.902] (II) AIGLX: Suspending AIGLX clients for VT switch
[163656.991] (II) Open ACPI successful (/var/run/acpid.socket)
[163656.991] (II) AIGLX: Resuming AIGLX clients after VT switch
[163657.046] (II) intel(0): EDID vendor "AUO", prod id 4766
[163657.047] (II) intel(0): Printing DDC gathered Modelines:
[163657.047] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[163657.170] (--) SynPS/2 Synaptics TouchPad: touchpad found
[163657.192] (II) Power Button: Device reopened after 1 attempts.
[163657.220] (II) Video Bus: Device reopened after 1 attempts.
[163657.232] (II) Video Bus: Device reopened after 1 attempts.
[163657.260] (II) Power Button: Device reopened after 1 attempts.
[163657.280] (II) Sleep Button: Device reopened after 1 attempts.
[163657.312] (II) HID 413c:8161: Device reopened after 1 attempts.
[163657.350] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device reopened after 1 attempts.
[163657.380] (II) Laptop_Integrated_Webcam_2M: Device reopened after 1 attempts.
[163657.412] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[163657.432] (II) Dell WMI hotkeys: Device reopened after 1 attempts.
[188769.203] (II) AIGLX: Suspending AIGLX clients for VT switch
[188789.273] (II) Open ACPI successful (/var/run/acpid.socket)
[188789.273] (II) AIGLX: Resuming AIGLX clients after VT switch
[188789.359] (II) intel(0): EDID vendor "AUO", prod id 4766
[188789.359] (II) intel(0): Printing DDC gathered Modelines:
[188789.359] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[188789.452] (--) SynPS/2 Synaptics TouchPad: touchpad found
[188789.512] (II) Power Button: Device reopened after 1 attempts.
[188789.532] (II) Video Bus: Device reopened after 1 attempts.
[188789.550] (II) Video Bus: Device reopened after 1 attempts.
[188789.562] (II) Power Button: Device reopened after 1 attempts.
[188789.590] (II) Sleep Button: Device reopened after 1 attempts.
[188789.612] (II) HID 413c:8161: Device reopened after 1 attempts.
[188789.652] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device reopened after 1 attempts.
[188789.702] (II) Laptop_Integrated_Webcam_2M: Device reopened after 1 attempts.
[188789.742] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[188789.782] (II) Dell WMI hotkeys: Device reopened after 1 attempts.
[190683.761] (II) AIGLX: Suspending AIGLX clients for VT switch
[190703.862] (II) Open ACPI successful (/var/run/acpid.socket)
[190703.862] (II) AIGLX: Resuming AIGLX clients after VT switch
[190703.908] (II) intel(0): EDID vendor "AUO", prod id 4766
[190703.908] (II) intel(0): Printing DDC gathered Modelines:
[190703.908] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[190704.011] (--) SynPS/2 Synaptics TouchPad: touchpad found
[190704.063] (II) Power Button: Device reopened after 1 attempts.
[190704.091] (II) Video Bus: Device reopened after 1 attempts.
[190704.111] (II) Video Bus: Device reopened after 1 attempts.
[190704.131] (II) Power Button: Device reopened after 1 attempts.
[190704.161] (II) Sleep Button: Device reopened after 1 attempts.
[190704.181] (II) HID 413c:8161: Device reopened after 1 attempts.
[190704.211] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device reopened after 1 attempts.
[190704.241] (II) Laptop_Integrated_Webcam_2M: Device reopened after 1 attempts.
[190704.281] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[190704.301] (II) Dell WMI hotkeys: Device reopened after 1 attempts.

``````
cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.29  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Wed Dec  8 12:27:39 PST 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS" "true"
    Modeline "1600x900@60" 120.42 1600 1632 2088 2120 900 918 927 946
EndSection

Section "Device"
    Identifier     "Device0"
#    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
#    BusID          "PCI:1:0:0"
#    Option         "NvAGP" "1" 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
     Modes      "1600x900" "1440x900" "1360x768" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by lidex on 2011-01-07
> **redy1966 said:**
> okidoki,

a few words regarding the output:
i know my config is not very clean yet, because i tried some possibilities to activate the nvidia card.
i have 5 or 6 xorg.conf for different modes, the posted one is the current.

also i try to remove the intel module, but i doesn't work

```
lsmod | grep -i intel_a
intel_agp              32462  2 i915

cat /etc/modprobe.d/blacklist-nvidia.conf 
# blacklist fuer nvidia treiber
blacklist agpgart-intel
blacklist agpgart
blacklist intel_agp

``````
sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GT216 [GeForce GT 330M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f9000000-f9ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fa000000-fa07ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fa400000-fa7fffff memory:b0000000-bfffffff ioport:f080(size=8)

``````
cat /var/log/Xorg.0.log
[148337.171] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[148337.171] X Protocol Version 11, Revision 0
[148337.171] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[148337.171] Current Operating System: Linux dellgurke 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[148337.171] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=fcdab5e4-eae0-4ed0-ad27-da9908ad314d ro quiet splash
[148337.171] Build Date: 16 September 2010  06:18:41PM
[148337.171] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[148337.171] Current version of pixman: 0.18.4
[148337.171]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[148337.171] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[148337.171] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  6 13:44:14 2011
[148337.182] (==) Using config file: "/etc/X11/xorg.conf"
[148337.182] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[148337.192] (==) ServerLayout "Layout0"
[148337.192] (**) |-->Screen "Screen0" (0)
[148337.192] (**) |   |-->Monitor "Monitor0"
[148337.192] (**) |   |-->Device "Device0"
[148337.192] (**) |-->Input Device "Keyboard0"
[148337.192] (**) |-->Input Device "Mouse0"
[148337.192] (==) Automatically adding devices
[148337.192] (==) Automatically enabling devices
[148337.193] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[148337.193]     Entry deleted from font path.
[148337.207] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[148337.207] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[148337.207] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[148337.207] (WW) Disabling Keyboard0
[148337.207] (WW) Disabling Mouse0
[148337.207] (II) Loader magic: 0x7d0200
[148337.207] (II) Module ABI versions:
[148337.207]     X.Org ANSI C Emulation: 0.4
[148337.207]     X.Org Video Driver: 8.0
[148337.207]     X.Org XInput driver : 11.0
[148337.207]     X.Org Server Extension : 4.0
[148337.209] (--) PCI:*(0:0:2:0) 8086:0046:1028:044f rev 24, Mem @ 0xfa400000/4194304, 0xb0000000/268435456, I/O @ 0x0000f080/8
[148337.209] (--) PCI: (0:1:0:0) 10de:0a29:1028:044f rev 162, Mem @ 0xf9000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[148337.209] (II) Open ACPI successful (/var/run/acpid.socket)
[148337.209] (II) LoadModule: "extmod"
[148337.218] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[148337.218] (II) Module extmod: vendor="X.Org Foundation"
[148337.218]     compiled for 1.9.0, module version = 1.0.0
[148337.218]     Module class: X.Org Server Extension
[148337.218]     ABI class: X.Org Server Extension, version 4.0
[148337.218] (II) Loading extension MIT-SCREEN-SAVER
[148337.218] (II) Loading extension XFree86-VidModeExtension
[148337.218] (II) Loading extension XFree86-DGA
[148337.218] (II) Loading extension DPMS
[148337.218] (II) Loading extension XVideo
[148337.218] (II) Loading extension XVideo-MotionCompensation
[148337.218] (II) Loading extension X-Resource
[148337.219] (II) LoadModule: "dbe"
[148337.219] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[148337.219] (II) Module dbe: vendor="X.Org Foundation"
[148337.219]     compiled for 1.9.0, module version = 1.0.0
[148337.219]     Module class: X.Org Server Extension
[148337.219]     ABI class: X.Org Server Extension, version 4.0
[148337.219] (II) Loading extension DOUBLE-BUFFER
[148337.219] (II) LoadModule: "glx"
[148337.219] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[148337.230] (II) Module glx: vendor="X.Org Foundation"
[148337.230]     compiled for 1.9.0, module version = 1.0.0
[148337.230]     ABI class: X.Org Server Extension, version 4.0
[148337.230] (==) AIGLX enabled
[148337.230] (II) Loading extension GLX
[148337.230] (II) LoadModule: "record"
[148337.231] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[148337.231] (II) Module record: vendor="X.Org Foundation"
[148337.231]     compiled for 1.9.0, module version = 1.13.0
[148337.231]     Module class: X.Org Server Extension
[148337.231]     ABI class: X.Org Server Extension, version 4.0
[148337.231] (II) Loading extension RECORD
[148337.231] (II) LoadModule: "dri"
[148337.231] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[148337.231] (II) Module dri: vendor="X.Org Foundation"
[148337.231]     compiled for 1.9.0, module version = 1.0.0
[148337.231]     ABI class: X.Org Server Extension, version 4.0
[148337.231] (II) Loading extension XFree86-DRI
[148337.231] (II) LoadModule: "dri2"
[148337.232] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[148337.232] (II) Module dri2: vendor="X.Org Foundation"
[148337.232]     compiled for 1.9.0, module version = 1.2.0
[148337.232]     ABI class: X.Org Server Extension, version 4.0
[148337.232] (II) Loading extension DRI2
[148337.232] (==) Matched intel as autoconfigured driver 0
[148337.232] (==) Matched vesa as autoconfigured driver 1
[148337.232] (==) Matched fbdev as autoconfigured driver 2
[148337.232] (==) Assigned the driver to the xf86ConfigLayout
[148337.232] (II) LoadModule: "intel"
[148337.232] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[148337.238] (II) Module intel: vendor="X.Org Foundation"
[148337.238]     compiled for 1.9.0, module version = 2.12.0
[148337.238]     Module class: X.Org Video Driver
[148337.238]     ABI class: X.Org Video Driver, version 8.0
[148337.238] (II) LoadModule: "vesa"
[148337.239] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[148337.239] (II) Module vesa: vendor="X.Org Foundation"
[148337.239]     compiled for 1.8.99.905, module version = 2.3.0
[148337.239]     Module class: X.Org Video Driver
[148337.239]     ABI class: X.Org Video Driver, version 8.0
[148337.239] (II) LoadModule: "fbdev"
[148337.239] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[148337.240] (II) Module fbdev: vendor="X.Org Foundation"
[148337.240]     compiled for 1.8.99.905, module version = 0.4.2
[148337.240]     ABI class: X.Org Video Driver, version 8.0
[148337.240] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[148337.240] (II) VESA: driver for VESA chipsets: vesa
[148337.240] (II) FBDEV: driver for framebuffer: fbdev
[148337.241] (--) using VT number 7

[148337.248] (WW) Falling back to old probe method for vesa
[148337.248] (WW) Falling back to old probe method for fbdev
[148337.248] (II) Loading sub module "fbdevhw"
[148337.248] (II) LoadModule: "fbdevhw"
[148337.249] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[148337.249] (II) Module fbdevhw: vendor="X.Org Foundation"
[148337.249]     compiled for 1.9.0, module version = 0.0.2
[148337.249]     ABI class: X.Org Video Driver, version 8.0
[148337.367] drmOpenDevice: node name is /dev/dri/card0
[148337.367] drmOpenDevice: open result is 9, (OK)
[148337.367] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[148337.367] drmOpenDevice: node name is /dev/dri/card0
[148337.367] drmOpenDevice: open result is 9, (OK)
[148337.367] drmOpenByBusid: drmOpenMinor returns 9
[148337.367] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[148337.367] drmOpenDevice: node name is /dev/dri/card1
[148337.367] drmOpenDevice: open result is 9, (OK)
[148337.367] drmOpenByBusid: drmOpenMinor returns 9
[148337.367] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[148337.367] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[148337.367] (==) intel(0): RGB weight 888
[148337.367] (==) intel(0): Default visual is TrueColor
[148337.367] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[148337.367] (--) intel(0): Chipset: "Arrandale"
[148337.367] (==) intel(0): video overlay key set to 0x101fe
[148337.384] (II) intel(0): Output VGA1 using monitor section Monitor0
[148337.384] (II) intel(0): Output LVDS1 has no monitor section
[148337.384] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[148337.394] (II) intel(0): Output HDMI1 has no monitor section
[148337.395] (II) intel(0): Output DP1 has no monitor section
[148337.411] (II) intel(0): EDID for output VGA1
[148337.411] (II) intel(0): EDID for output LVDS1
[148337.411] (II) intel(0): Manufacturer: AUO  Model: 129e  Serial#: 0
[148337.411] (II) intel(0): Year: 2009  Week: 1
[148337.411] (II) intel(0): EDID Version: 1.3
[148337.411] (II) intel(0): Digital Display Input
[148337.411] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[148337.412] (II) intel(0): Gamma: 2.20
[148337.412] (II) intel(0): No DPMS capabilities specified
[148337.412] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[148337.412] (II) intel(0): First detailed timing is preferred mode
[148337.412] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.325 greenY: 0.570
[148337.412] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[148337.412] (II) intel(0): Manufacturer's mask: 0
[148337.412] (II) intel(0): Supported detailed timing:
[148337.412] (II) intel(0): clock: 110.0 MHz   Image Size:  382 x 214 mm
[148337.412] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 2000 h_border: 0
[148337.412] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 912 v_border: 0
[148337.412] (II) intel(0): Supported detailed timing:
[148337.412] (II) intel(0): clock: 110.0 MHz   Image Size:  382 x 214 mm
[148337.412] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 2000 h_border: 0
[148337.412] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 912 v_border: 0
[148337.412] (II) intel(0):  0D41C&#65533;B173RW1
[148337.412] (II) intel(0): Unknown vendor-specific block 0
[148337.412] (II) intel(0): EDID (in hex):
[148337.412] (II) intel(0):     00ffffffffffff0006af9e1200000000
[148337.412] (II) intel(0):     01130103902615780ac4959e57539226
[148337.412] (II) intel(0):     0f505400000001010101010101010101
[148337.412] (II) intel(0):     010101010101f82a409061840c303020
[148337.412] (II) intel(0):     36007ed61000001af82a409061840c30
[148337.412] (II) intel(0):     302036007ed61000001a000000fe0030
[148337.412] (II) intel(0):     44343143804231373352573100000000
[148337.412] (II) intel(0):     00000000000000000002010a20200054
[148337.412] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[148337.412] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[148337.412] (II) intel(0): Printing probed modes for output LVDS1
[148337.412] (II) intel(0): Modeline "1600x900"x60.3  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148337.412] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[148337.412] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[148337.412] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[148337.412] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[148337.412] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[148337.412] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[148337.412] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[148337.412] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[148337.421] (II) intel(0): EDID for output HDMI1
[148337.422] (II) intel(0): EDID for output DP1
[148337.422] (II) intel(0): Output VGA1 disconnected
[148337.422] (II) intel(0): Output LVDS1 connected
[148337.422] (II) intel(0): Output HDMI1 disconnected
[148337.422] (II) intel(0): Output DP1 disconnected
[148337.422] (II) intel(0): Using user preference for initial modes
[148337.422] (II) intel(0): Output LVDS1 using initial mode 1600x900
[148337.422] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[148337.422] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[148337.422] (==) intel(0): DPI set to (96, 96)
[148337.422] (II) Loading sub module "fb"
[148337.422] (II) LoadModule: "fb"
[148337.423] (II) Loading /usr/lib/xorg/modules/libfb.so
[148337.436] (II) Module fb: vendor="X.Org Foundation"
[148337.436]     compiled for 1.9.0, module version = 1.0.0
[148337.436]     ABI class: X.Org ANSI C Emulation, version 0.4
[148337.436] (II) UnloadModule: "vesa"
[148337.436] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[148337.436] (II) UnloadModule: "fbdev"
[148337.436] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[148337.436] (II) UnloadModule: "fbdevhw"
[148337.436] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[148337.436] (==) Depth 24 pixmap format is 32 bpp
[148337.436] (II) intel(0): [DRI2] Setup complete
[148337.436] (II) intel(0): [DRI2]   DRI driver: i965
[148337.436] (**) intel(0): Tiling enabled
[148337.436] (**) intel(0): SwapBuffers wait enabled
[148337.436] (==) intel(0): VideoRam: 262144 KB
[148337.436] (II) intel(0): Allocated new frame buffer 1600x900 stride 6656, tiled
[148337.447] (II) UXA(0): Driver registered support for the following operations:
[148337.447] (II)         solid
[148337.447] (II)         copy
[148337.447] (II)         composite (RENDER acceleration)
[148337.447] (II)         put_image
[148337.447] (II)         get_image
[148337.448] (==) intel(0): Backing store disabled
[148337.448] (==) intel(0): Silken mouse enabled
[148337.448] (II) intel(0): Initializing HW Cursor
[148337.492] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[148337.494] (**) intel(0): DPMS enabled
[148337.494] (==) intel(0): Intel XvMC decoder enabled
[148337.494] (II) intel(0): Set up textured video
[148337.494] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[148337.494] (II) intel(0): direct rendering: DRI2 Enabled
[148337.494] (--) RandR disabled
[148337.494] (II) Initializing built-in extension Generic Event Extension
[148337.494] (II) Initializing built-in extension SHAPE
[148337.494] (II) Initializing built-in extension MIT-SHM
[148337.494] (II) Initializing built-in extension XInputExtension
[148337.494] (II) Initializing built-in extension XTEST
[148337.494] (II) Initializing built-in extension BIG-REQUESTS
[148337.494] (II) Initializing built-in extension SYNC
[148337.494] (II) Initializing built-in extension XKEYBOARD
[148337.494] (II) Initializing built-in extension XC-MISC
[148337.494] (II) Initializing built-in extension SECURITY
[148337.494] (II) Initializing built-in extension XINERAMA
[148337.494] (II) Initializing built-in extension XFIXES
[148337.494] (II) Initializing built-in extension RENDER
[148337.494] (II) Initializing built-in extension RANDR
[148337.494] (II) Initializing built-in extension COMPOSITE
[148337.494] (II) Initializing built-in extension DAMAGE
[148337.494] (II) Initializing built-in extension GESTURE
[148337.505] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[148337.505] (II) AIGLX: enabled GLX_INTEL_swap_event
[148337.505] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[148337.505] (II) AIGLX: enabled GLX_SGI_make_current_read
[148337.505] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[148337.505] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[148337.505] (II) GLX: Initialized DRI2 GL provider for screen 0
[148337.505] (II) intel(0): Setting screen physical size to 423 x 238
[148337.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[148337.613] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[148337.613] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[148337.613] (II) LoadModule: "evdev"
[148337.613] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[148337.613] (II) Module evdev: vendor="X.Org Foundation"
[148337.613]     compiled for 1.9.0, module version = 2.3.2
[148337.613]     Module class: X.Org XInput Driver
[148337.613]     ABI class: X.Org XInput driver, version 11.0
[148337.613] (**) Power Button: always reports core events
[148337.613] (**) Power Button: Device: "/dev/input/event3"
[148337.671] (II) Power Button: Found keys
[148337.671] (II) Power Button: Configuring as keyboard
[148337.671] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[148337.671] (**) Option "xkb_rules" "evdev"
[148337.671] (**) Option "xkb_model" "evdev"
[148337.671] (**) Option "xkb_layout" "de"
[148337.674] (II) XKB: reuse xkmfile /var/lib/xkb/server-1B5353734E7854C1F2B0553E65A16986C9AAC402.xkm
[148337.676] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[148337.676] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[148337.676] (**) Video Bus: always reports core events
[148337.676] (**) Video Bus: Device: "/dev/input/event11"
[148337.753] (II) Video Bus: Found keys
[148337.753] (II) Video Bus: Configuring as keyboard
[148337.753] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[148337.753] (**) Option "xkb_rules" "evdev"
[148337.753] (**) Option "xkb_model" "evdev"
[148337.753] (**) Option "xkb_layout" "de"
[148337.754] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[148337.755] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[148337.755] (**) Video Bus: always reports core events
[148337.755] (**) Video Bus: Device: "/dev/input/event10"
[148337.833] (II) Video Bus: Found keys
[148337.833] (II) Video Bus: Configuring as keyboard
[148337.833] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[148337.833] (**) Option "xkb_rules" "evdev"
[148337.833] (**) Option "xkb_model" "evdev"
[148337.833] (**) Option "xkb_layout" "de"
[148337.836] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[148337.836] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[148337.836] (**) Power Button: always reports core events
[148337.836] (**) Power Button: Device: "/dev/input/event0"
[148337.913] (II) Power Button: Found keys
[148337.913] (II) Power Button: Configuring as keyboard
[148337.913] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[148337.913] (**) Option "xkb_rules" "evdev"
[148337.913] (**) Option "xkb_model" "evdev"
[148337.913] (**) Option "xkb_layout" "de"
[148337.914] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[148337.914] (II) No input driver/identifier specified (ignoring)
[148337.914] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[148337.914] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[148337.914] (**) Sleep Button: always reports core events
[148337.914] (**) Sleep Button: Device: "/dev/input/event2"
[148338.033] (II) Sleep Button: Found keys
[148338.033] (II) Sleep Button: Configuring as keyboard
[148338.033] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[148338.033] (**) Option "xkb_rules" "evdev"
[148338.033] (**) Option "xkb_model" "evdev"
[148338.033] (**) Option "xkb_layout" "de"
[148338.037] (II) config/udev: Adding input device HID 413c:8161 (/dev/input/event6)
[148338.037] (**) HID 413c:8161: Applying InputClass "evdev keyboard catchall"
[148338.037] (**) HID 413c:8161: always reports core events
[148338.037] (**) HID 413c:8161: Device: "/dev/input/event6"
[148338.113] (II) HID 413c:8161: Found keys
[148338.113] (II) HID 413c:8161: Configuring as keyboard
[148338.113] (II) XINPUT: Adding extended input device "HID 413c:8161" (type: KEYBOARD)
[148338.113] (**) Option "xkb_rules" "evdev"
[148338.113] (**) Option "xkb_model" "evdev"
[148338.113] (**) Option "xkb_layout" "de"
[148338.115] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
[148338.115] (II) No input driver/identifier specified (ignoring)
[148338.115] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event13)
[148338.115] (II) No input driver/identifier specified (ignoring)
[148338.117] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event5)
[148338.117] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[148338.117] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[148338.118] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event5"
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[148338.193] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[148338.193] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[148338.194] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[148338.194] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[148338.194] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[148338.194] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[148338.194] (II) No input driver/identifier specified (ignoring)
[148338.195] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event7)
[148338.195] (**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
[148338.195] (**) Laptop_Integrated_Webcam_2M: always reports core events
[148338.195] (**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event7"
[148338.273] (II) Laptop_Integrated_Webcam_2M: Found keys
[148338.273] (II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
[148338.273] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
[148338.273] (**) Option "xkb_rules" "evdev"
[148338.273] (**) Option "xkb_model" "evdev"
[148338.273] (**) Option "xkb_layout" "de"
[148338.277] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[148338.277] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[148338.277] (**) AT Translated Set 2 keyboard: always reports core events
[148338.277] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[148338.353] (II) AT Translated Set 2 keyboard: Found keys
[148338.353] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[148338.353] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[148338.353] (**) Option "xkb_rules" "evdev"
[148338.353] (**) Option "xkb_model" "evdev"
[148338.353] (**) Option "xkb_layout" "de"
[148338.354] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[148338.354] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[148338.354] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[148338.354] (II) LoadModule: "synaptics"
[148338.354] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[148338.354] (II) Module synaptics: vendor="X.Org Foundation"
[148338.354]     compiled for 1.9.0, module version = 1.2.2
[148338.354]     Module class: X.Org XInput Driver
[148338.354]     ABI class: X.Org XInput driver, version 11.0
[148338.354] (II) Synaptics touchpad driver version 1.2.2
[148338.355] (**) Option "Device" "/dev/input/event9"
[148338.793] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5650
[148338.793] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4710
[148338.793] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[148338.793] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[148338.793] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[148339.113] (--) SynPS/2 Synaptics TouchPad: touchpad found
[148339.113] (**) SynPS/2 Synaptics TouchPad: always reports core events
[148339.273] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[148339.273] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[148339.273] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[148339.273] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[148339.274] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[148339.513] (--) SynPS/2 Synaptics TouchPad: touchpad found
[148339.514] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[148339.514] (II) No input driver/identifier specified (ignoring)
[148339.518] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[148339.518] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[148339.518] (**) Dell WMI hotkeys: always reports core events
[148339.518] (**) Dell WMI hotkeys: Device: "/dev/input/event8"
[148339.593] (II) Dell WMI hotkeys: Found keys
[148339.593] (II) Dell WMI hotkeys: Configuring as keyboard
[148339.593] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[148339.593] (**) Option "xkb_rules" "evdev"
[148339.593] (**) Option "xkb_model" "evdev"
[148339.593] (**) Option "xkb_layout" "de"
[148340.225] (II) intel(0): EDID vendor "AUO", prod id 4766
[148340.226] (II) intel(0): Printing DDC gathered Modelines:
[148340.226] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148340.255] (II) intel(0): EDID vendor "AUO", prod id 4766
[148340.255] (II) intel(0): Printing DDC gathered Modelines:
[148340.255] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148340.283] (II) intel(0): EDID vendor "AUO", prod id 4766
[148340.283] (II) intel(0): Printing DDC gathered Modelines:
[148340.283] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148340.311] (II) intel(0): EDID vendor "AUO", prod id 4766
[148340.311] (II) intel(0): Printing DDC gathered Modelines:
[148340.311] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148346.655] (II) intel(0): EDID vendor "AUO", prod id 4766
[148346.655] (II) intel(0): Printing DDC gathered Modelines:
[148346.655] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148346.684] (II) intel(0): EDID vendor "AUO", prod id 4766
[148346.684] (II) intel(0): Printing DDC gathered Modelines:
[148346.684] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148346.712] (II) intel(0): EDID vendor "AUO", prod id 4766
[148346.712] (II) intel(0): Printing DDC gathered Modelines:
[148346.712] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148346.740] (II) intel(0): EDID vendor "AUO", prod id 4766
[148346.740] (II) intel(0): Printing DDC gathered Modelines:
[148346.740] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148347.293] (II) intel(0): EDID vendor "AUO", prod id 4766
[148347.293] (II) intel(0): Printing DDC gathered Modelines:
[148347.293] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[148352.344] (II) intel(0): EDID vendor "AUO", prod id 4766
[148352.344] (II) intel(0): Printing DDC gathered Modelines:
[148352.344] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[150223.274] (II) intel(0): EDID vendor "AUO", prod id 4766
[150223.274] (II) intel(0): Printing DDC gathered Modelines:
[150223.274] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[154394.497] (II) intel(0): EDID vendor "AUO", prod id 4766
[154394.497] (II) intel(0): Printing DDC gathered Modelines:
[154394.497] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[156400.728] (II) intel(0): EDID vendor "AUO", prod id 4766
[156400.728] (II) intel(0): Printing DDC gathered Modelines:
[156400.728] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[163636.902] (II) AIGLX: Suspending AIGLX clients for VT switch
[163656.991] (II) Open ACPI successful (/var/run/acpid.socket)
[163656.991] (II) AIGLX: Resuming AIGLX clients after VT switch
[163657.046] (II) intel(0): EDID vendor "AUO", prod id 4766
[163657.047] (II) intel(0): Printing DDC gathered Modelines:
[163657.047] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[163657.170] (--) SynPS/2 Synaptics TouchPad: touchpad found
[163657.192] (II) Power Button: Device reopened after 1 attempts.
[163657.220] (II) Video Bus: Device reopened after 1 attempts.
[163657.232] (II) Video Bus: Device reopened after 1 attempts.
[163657.260] (II) Power Button: Device reopened after 1 attempts.
[163657.280] (II) Sleep Button: Device reopened after 1 attempts.
[163657.312] (II) HID 413c:8161: Device reopened after 1 attempts.
[163657.350] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device reopened after 1 attempts.
[163657.380] (II) Laptop_Integrated_Webcam_2M: Device reopened after 1 attempts.
[163657.412] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[163657.432] (II) Dell WMI hotkeys: Device reopened after 1 attempts.
[188769.203] (II) AIGLX: Suspending AIGLX clients for VT switch
[188789.273] (II) Open ACPI successful (/var/run/acpid.socket)
[188789.273] (II) AIGLX: Resuming AIGLX clients after VT switch
[188789.359] (II) intel(0): EDID vendor "AUO", prod id 4766
[188789.359] (II) intel(0): Printing DDC gathered Modelines:
[188789.359] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[188789.452] (--) SynPS/2 Synaptics TouchPad: touchpad found
[188789.512] (II) Power Button: Device reopened after 1 attempts.
[188789.532] (II) Video Bus: Device reopened after 1 attempts.
[188789.550] (II) Video Bus: Device reopened after 1 attempts.
[188789.562] (II) Power Button: Device reopened after 1 attempts.
[188789.590] (II) Sleep Button: Device reopened after 1 attempts.
[188789.612] (II) HID 413c:8161: Device reopened after 1 attempts.
[188789.652] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device reopened after 1 attempts.
[188789.702] (II) Laptop_Integrated_Webcam_2M: Device reopened after 1 attempts.
[188789.742] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[188789.782] (II) Dell WMI hotkeys: Device reopened after 1 attempts.
[190683.761] (II) AIGLX: Suspending AIGLX clients for VT switch
[190703.862] (II) Open ACPI successful (/var/run/acpid.socket)
[190703.862] (II) AIGLX: Resuming AIGLX clients after VT switch
[190703.908] (II) intel(0): EDID vendor "AUO", prod id 4766
[190703.908] (II) intel(0): Printing DDC gathered Modelines:
[190703.908] (II) intel(0): Modeline "1600x900"x0.0  110.00  1600 1648 1680 2000  900 903 909 912 +hsync -vsync (55.0 kHz)
[190704.011] (--) SynPS/2 Synaptics TouchPad: touchpad found
[190704.063] (II) Power Button: Device reopened after 1 attempts.
[190704.091] (II) Video Bus: Device reopened after 1 attempts.
[190704.111] (II) Video Bus: Device reopened after 1 attempts.
[190704.131] (II) Power Button: Device reopened after 1 attempts.
[190704.161] (II) Sleep Button: Device reopened after 1 attempts.
[190704.181] (II) HID 413c:8161: Device reopened after 1 attempts.
[190704.211] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device reopened after 1 attempts.
[190704.241] (II) Laptop_Integrated_Webcam_2M: Device reopened after 1 attempts.
[190704.281] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[190704.301] (II) Dell WMI hotkeys: Device reopened after 1 attempts.

``````
cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.29  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Wed Dec  8 12:27:39 PST 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS" "true"
    Modeline "1600x900@60" 120.42 1600 1632 2088 2120 900 918 927 946
EndSection

Section "Device"
    Identifier     "Device0"
#    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
#    BusID          "PCI:1:0:0"
#    Option         "NvAGP" "1" 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
     Modes      "1600x900" "1440x900" "1360x768" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

You might try removing the intel xorg driver:
```
sudo apt-get purge xserver-xorg-video-intel
```
And what is your full lsmod output:
```
lsmod
```

---

### Post by redy1966 on 2011-01-07
ok, tried and failed.

first i do "apt-get install nvidia-current" & "apt-get autoremove" for some old nvidia settings. then a "apt-get purge xserver-...."
reboot

here my xserver log:

```
cat /var/log/Xorg.0.log
[    12.965] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    12.965] X Protocol Version 11, Revision 0
[    12.965] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    12.965] Current Operating System: Linux dellgurke 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    12.965] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=fcdab5e4-eae0-4ed0-ad27-da9908ad314d ro quiet splash
[    12.965] Build Date: 16 September 2010  06:18:41PM
[    12.965] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    12.965] Current version of pixman: 0.18.4
[    12.965]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    12.965] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.965] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  7 11:55:13 2011
[    12.965] (==) Using config file: "/etc/X11/xorg.conf"
[    12.965] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.966] (==) ServerLayout "Layout0"
[    12.966] (**) |-->Screen "Screen0" (0)
[    12.966] (**) |   |-->Monitor "Monitor0"
[    12.966] (**) |   |-->Device "Device0"
[    12.966] (**) |-->Input Device "Keyboard0"
[    12.966] (**) |-->Input Device "Mouse0"
[    12.966] (==) Automatically adding devices
[    12.966] (==) Automatically enabling devices
[    12.966] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.966]     Entry deleted from font path.
[    12.966] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    12.966] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.966] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    12.966] (WW) Disabling Keyboard0
[    12.966] (WW) Disabling Mouse0
[    12.966] (II) Loader magic: 0x7d0200
[    12.966] (II) Module ABI versions:
[    12.966]     X.Org ANSI C Emulation: 0.4
[    12.966]     X.Org Video Driver: 8.0
[    12.966]     X.Org XInput driver : 11.0
[    12.966]     X.Org Server Extension : 4.0
[    12.967] (--) PCI:*(0:0:2:0) 8086:0046:1028:044f rev 24, Mem @ 0xfa400000/4194304, 0xb0000000/268435456, I/O @ 0x0000f080/8
[    12.967] (--) PCI: (0:1:0:0) 10de:0a29:1028:044f rev 162, Mem @ 0xf9000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    12.967] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    12.967] (II) LoadModule: "extmod"
[    13.010] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.010] (II) Module extmod: vendor="X.Org Foundation"
[    13.010]     compiled for 1.9.0, module version = 1.0.0
[    13.010]     Module class: X.Org Server Extension
[    13.010]     ABI class: X.Org Server Extension, version 4.0
[    13.010] (II) Loading extension MIT-SCREEN-SAVER
[    13.010] (II) Loading extension XFree86-VidModeExtension
[    13.011] (II) Loading extension XFree86-DGA
[    13.011] (II) Loading extension DPMS
[    13.011] (II) Loading extension XVideo
[    13.011] (II) Loading extension XVideo-MotionCompensation
[    13.011] (II) Loading extension X-Resource
[    13.011] (II) LoadModule: "dbe"
[    13.011] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.011] (II) Module dbe: vendor="X.Org Foundation"
[    13.011]     compiled for 1.9.0, module version = 1.0.0
[    13.011]     Module class: X.Org Server Extension
[    13.011]     ABI class: X.Org Server Extension, version 4.0
[    13.011] (II) Loading extension DOUBLE-BUFFER
[    13.011] (II) LoadModule: "glx"
[    13.011] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    13.788] (II) Module glx: vendor="NVIDIA Corporation"
[    13.806]     compiled for 4.0.2, module version = 1.0.0
[    13.806]     Module class: X.Org Server Extension
[    13.806] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    13.806] (II) Loading extension GLX
[    13.806] (II) LoadModule: "record"
[    13.806] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.806] (II) Module record: vendor="X.Org Foundation"
[    13.806]     compiled for 1.9.0, module version = 1.13.0
[    13.806]     Module class: X.Org Server Extension
[    13.806]     ABI class: X.Org Server Extension, version 4.0
[    13.806] (II) Loading extension RECORD
[    13.806] (II) LoadModule: "dri"
[    13.806] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.807] (II) Module dri: vendor="X.Org Foundation"
[    13.807]     compiled for 1.9.0, module version = 1.0.0
[    13.807]     ABI class: X.Org Server Extension, version 4.0
[    13.807] (II) Loading extension XFree86-DRI
[    13.807] (II) LoadModule: "dri2"
[    13.807] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.807] (II) Module dri2: vendor="X.Org Foundation"
[    13.807]     compiled for 1.9.0, module version = 1.2.0
[    13.807]     ABI class: X.Org Server Extension, version 4.0
[    13.807] (II) Loading extension DRI2
[    13.807] (II) LoadModule: "nvidia"
[    13.807] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    13.893] (II) Module nvidia: vendor="NVIDIA Corporation"
[    13.894]     compiled for 4.0.2, module version = 1.0.0
[    13.894]     Module class: X.Org Video Driver
[    13.916] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    13.916] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    13.916] (++) using VT number 7

[    13.917] (II) Loading sub module "fb"
[    13.917] (II) LoadModule: "fb"
[    13.917] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.917] (II) Module fb: vendor="X.Org Foundation"
[    13.917]     compiled for 1.9.0, module version = 1.0.0
[    13.917]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.917] (II) Loading sub module "wfb"
[    13.917] (II) LoadModule: "wfb"
[    13.917] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    13.934] (II) Module wfb: vendor="X.Org Foundation"
[    13.934]     compiled for 1.9.0, module version = 1.0.0
[    13.934]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.934] (II) Loading sub module "ramdac"
[    13.934] (II) LoadModule: "ramdac"
[    13.934] (II) Module "ramdac" already built-in
[    13.937] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    13.937] (==) NVIDIA(0): RGB weight 888
[    13.937] (==) NVIDIA(0): Default visual is TrueColor
[    13.937] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.937] (**) NVIDIA(0): Option "NvAGP" "1"
[    13.950] (**) NVIDIA(0): Enabling RENDER acceleration
[    13.950] (**) NVIDIA(0): Use of NVIDIA internal AGP requested
[    13.950] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    13.950] (II) NVIDIA(0):     enabled.
[    14.192] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
[    14.192] (EE) NVIDIA(0):     Please check your system's kernel log for additional error
[    14.192] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[    14.192] (EE) NVIDIA(0):     README for additional information.
[    14.192] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    14.192] (II) UnloadModule: "nvidia"
[    14.192] (II) UnloadModule: "wfb"
[    14.192] (II) UnloadModule: "fb"
[    14.192] (EE) Screen(s) found, but none have a usable configuration.
[    14.192] 
Fatal server error:
[    14.192] no screens found
[    14.192] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    14.192] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.192] 
[    14.226]  ddxSigGiveUp: Closing log

```

my kernel log

cat /var/log/kern.log | grep -i intel

```
Jan  7 12:04:54 dellgurke kernel: [    0.005833] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
Jan  7 12:04:54 dellgurke kernel: [    0.146561] CPU0: Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GHz stepping 05
Jan  7 12:04:54 dellgurke kernel: [    1.269330] intel_idle: MWAIT substates: 0x1120
Jan  7 12:04:54 dellgurke kernel: [    1.269332] intel_idle: v0.4 model 0x25
Jan  7 12:04:54 dellgurke kernel: [    1.269333] intel_idle: lapic_timer_reliable_states 0xffffffff
Jan  7 12:04:54 dellgurke kernel: [    1.272625] ACPI: acpi_idle yielding to intel_idle
Jan  7 12:04:54 dellgurke kernel: [    2.612944] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input5
Jan  7 12:04:54 dellgurke kernel: [    2.613109] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1.3/input0
Jan  7 12:04:54 dellgurke kernel: [   11.611066] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
Jan  7 12:04:54 dellgurke kernel: [   11.612086] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Jan  7 12:04:54 dellgurke kernel: [   11.746059] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
Jan  7 12:04:54 dellgurke kernel: [   11.746096] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
Jan  7 12:04:54 dellgurke kernel: [   11.746118] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan  7 12:04:54 dellgurke kernel: [   11.746277] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
Jan  7 12:04:54 dellgurke kernel: [   11.747480] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
Jan  7 12:04:54 dellgurke kernel: [   11.813585] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan  7 12:04:54 dellgurke kernel: [   11.813674] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
Jan  7 12:04:54 dellgurke kernel: [   11.813722] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jan  7 12:04:54 dellgurke kernel: [   12.948960] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Jan  7 12:04:54 dellgurke kernel: [   12.949041] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Jan  7 12:04:54 dellgurke kernel: [   12.949254] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  7 12:04:54 dellgurke kernel: [   12.949260] hda_intel: Disable MSI for Nvidia chipset
Jan  7 12:04:54 dellgurke kernel: [   12.949305] HDA Intel 0000:01:00.1: setting latency timer to 64
Jan  7 12:04:54 dellgurke kernel: [   14.062336] fb0: inteldrmfb frame buffer device
Jan  7 12:05:17 dellgurke kernel: [   37.245112] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

```

cat /var/log/kern.log | grep -i nvidia

```
Jan  7 12:04:54 dellgurke kernel: [   12.612394] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
Jan  7 12:04:54 dellgurke kernel: [   12.612405] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  7 12:04:54 dellgurke kernel: [   12.612421] nvidia 0000:01:00.0: setting latency timer to 64
Jan  7 12:04:54 dellgurke kernel: [   12.612590] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
Jan  7 12:04:54 dellgurke kernel: [   12.949260] hda_intel: Disable MSI for Nvidia chipset

```


my complete lsmod output

```
lsmod
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_nvhdmi    15451  4 
joydev                 11395  0 
nvidia              10221046  0 
btusb                  12929  0 
bluetooth              59245  1 btusb
snd_hda_codec_idt      64667  1 
i915                  334267  4 
snd_seq_midi            5932  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            22207  1 snd_seq_midi
drm_kms_helper         32836  1 i915
drm                   206230  2 i915,drm_kms_helper
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     8732  0 
dell_wmi_aio            2097  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
wl                   1965231  0 
dell_laptop             6722  0 
dcdbas                  6910  1 dell_laptop
intel_ips              13252  0 
dell_wmi                3372  0 
psmouse                62080  0 
serio_raw               4910  0 
snd                    64181  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
intel_agp              32462  2 i915
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
lp                     10201  0 
output                  2527  1 video
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lib80211                6175  2 lib80211_crypt_tkip,wl
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84710  1 usbhid
ahci                   22210  2 
sdhci_pci               7765  0 
firewire_ohci          24615  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
firewire_core          54327  1 firewire_ohciintel_agp        
crc_itu_t               1739  1 firewire_core
libahci                26052  1 ahci
r8169                  42254  0 
mii                     5261  1 r8169

```

q:
what means the kernel log msg "hda_intel: Disable MSI for Nvidia chipset" ?
i blacklisted the agpgart-intel, but it has no effect. the modul will loaded.

Jan  7 12:04:54 dellgurke kernel: [   11.611066] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset

redy@dellgurke:~$ lsmod | grep -i intel_agp
intel_agp              32462  2 i915
redy@dellgurke:~$ sudo modprobe -r intel_agp 
FATAL: Module intel_agp is in use.

hmmm  :confused:

---

### Post by lidex on 2011-01-07
There is a huge difference in Xorg.0.log. X is trying to load nvidia driver and no intel there. Just need to find out why it's failing.
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
[    14.192] (EE) NVIDIA(0):     Please check your system's kernel log for additional error
[    14.192] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[    14.192] (EE) NVIDIA(0):     README for additional information.
[    14.192] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    14.192] (II) UnloadModule: "nvidia"
[    14.192] (II) UnloadModule: "wfb"
[    14.192] (II) UnloadModule: "fb"
[    14.192] (EE) Screen(s) found, but none have a usable configuration.
[    14.192] 
Fatal server error:
[    14.192] no screens found
```
Believe it or not that is progress.
Have you tried to disable onboard graphics chip (in bios)? My bios also has an option
to select default video - agp, pci. Generally I think it's best when installing graphics drivers 
to remove the current one, remove xorg.conf, then reboot. Then install new driver. Also you want to grep nvidia
in kernel log.

---

### Post by redy1966 on 2011-01-07
> **lidex said:**
> 
Believe it or not that is progress.
Have you tried to disable onboard graphics chip (in bios)? My bios also has an option
to select default video - agp, pci.

i know the difficulty with this 2 gpu 
unfortunatly i have no possibility to set anything in my BIOS :( thats very poor

---

### Post by lidex on 2011-01-07
Do you mean the bios is locked by the manufacturer? There is probably a way to get around that - I've done it before.
Have a look here: [http://www.techspot.com/vb/topic90285.html](http://www.techspot.com/vb/topic90285.html)

---

### Post by redy1966 on 2011-01-07
that's not a password problem pwd is not set).
my BIOS (dell a09) have no option to disable the onboard intel gpu. :(
it exist a newer version (A10), but they have also no option to setup the gpu config.

that what i mean with an poor BIOS...

---

### Post by lidex on 2011-01-07
> **redy1966 said:**
> that's not a password problem pwd is not set).
my BIOS (dell a09) have no option to disable the onboard intel gpu. :(
it exist a newer version (A10), but they have also no option to setup the gpu config.

that what i mean with an poor BIOS...
OK, I'm a little slow here. If A10 allows you to disable onboard graphics, that's all you need. You don't need to do anything in bios for the nvidia card.

---

### Post by redy1966 on 2011-01-08
ok, end of the road...

nvidia with optimus chipset will not work on dell vostro 3500/3700
if anyone would buy this laptop: hands off

dell dont support linux for vostro hardware
dell provides no BIOS with the possilbility to deactivate the intel GPU
nvidia have no plan to support OPTIMUS in linux
[http://www.nvnews.net/vbulletin/showthread.php?t=144750](http://www.nvnews.net/vbulletin/showthread.php?t=144750)

so, ich have to wait for kernelmodul vga_switcheroo 
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=6a9ee8af344e3bd7dbd61e67037096cdf7f83289](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=6a9ee8af344e3bd7dbd61e67037096cdf7f83289)

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

at the moment, the module supports only ATI cards, hope NVIDIA support will follow.

one thing i don't understand:
[http://webapps.ubuntu.com/certification/hardware/201001-4961/](http://webapps.ubuntu.com/certification/hardware/201001-4961/)

damn, why is the vostro certified on this page? that's not true !

cu
redy

---

### Post by dalien26 on 2011-05-11
i have exactly the same problem :(
no solution yet ?

the intel graphic card is certified, not the nvidia

---

