---
title: "After coming back from suspend / console mode to GUI desktop position out of screen"
date: 2012-05-28
forum: Desktop Environments
---

### Post by athlon2000 on 2012-05-28
Hi all,
I have the following problem:
Everytime I come back to the GUI the desktop is horizontally moved out of the screen bounds. I only see a small band of the desktop on the left side, the rest of the screen is black. When I start the system up everything is okay, so this only seems to happen when the screen resolution/positioning is updated.
It happens when I come back from the suspend/hibernate mode, but also when I come back from the console mode: I press ctrl+alt+F6 -> the console comes up as desired, everything seems to be fine, but when I hit ctrl+alt+F7 to go back to the Desktop mode the whole desktop is moved to the left side, as described above.

I've already tried googling, but I wasn't able to find a bearable solution so far, though it could be I didn't use the right keywords.
My current solution is to blindly start the terminal and type the commands
xrandr -o left
-> this turns the screen left and I see the whole desktop again
then I type:
xrandr -o normal
and everything is fine again. I guess xrandr could do it without tilting the screen left first too somehow, but I'm pretty new to Ubuntu so please forgive me.

Could it have something to do with my graphics driver? I'm using the ATI/AMD: proprietary FGLRX-driver which should be pretty much up to date. 

Since I'm using a laptop I also tried hitting FN+F5 because I thought this could update the screen settings somehow, but it doesn't help either.

---

### Post by shafi.dude99 on 2012-05-28
would like to have some more information about it ..

open terminal and write the following commands and paste the output to post

lspci -v | grep "VGA"

cat /var/log/Xorg.0.log

---

### Post by athlon2000 on 2012-05-28
> **shafi.dude99 said:**
> would like to have some more information about it ..

open terminal and write the following commands and paste the output to post

lspci -v | grep "VGA"

cat /var/log/Xorg.0.log

Thank you for your response. Here are the results:

```
$ lspci -v| grep "VGA"
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series] (prog-if 00 [VGA controller])
``````
$ cat /var/log/Xorg.0.log
[    27.966] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    27.966] X Protocol Version 11, Revision 0
[    27.966] Build Operating System: Linux 2.6.24-31-server i686 Ubuntu
[    27.966] Current Operating System: Linux ubuntu 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686
[    27.966] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=D2329FE3329FCB3D loop=/ubuntu/disks/root.disk ro splash quiet splash vt.handoff=7
[    27.966] Build Date: 07 May 2012  11:39:37PM
[    27.966] xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see http://www.ubuntu.com/support) 
[    27.966] Current version of pixman: 0.24.4
[    27.966]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    27.966] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.967] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May 28 12:26:56 2012
[    28.014] (==) Using config file: "/etc/X11/xorg.conf"
[    28.014] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.341] (==) ServerLayout "amdcccle Layout"
[    28.341] (**) |-->Screen "amdcccle-Screen[1]-0" (0)
[    28.341] (**) |   |-->Monitor "<default monitor>"
[    28.365] (**) |   |-->Device "amdcccle-Device[1]-0"
[    28.365] (==) No monitor specified for screen "amdcccle-Screen[1]-0".
        Using a default monitor configuration.
[    28.365] (==) Automatically adding devices
[    28.365] (==) Automatically enabling devices
[    28.526] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.526]    Entry deleted from font path.
[    28.691] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    28.691] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.691] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.691] (II) Loader magic: 0xb771c5a0
[    28.691] (II) Module ABI versions:
[    28.691]    X.Org ANSI C Emulation: 0.4
[    28.691]    X.Org Video Driver: 11.0
[    28.691]    X.Org XInput driver : 16.0
[    28.691]    X.Org Server Extension : 6.0
[    28.692] (--) PCI:*(0:1:0:0) 1002:68c1:1179:fd12 rev 0, Mem @ 0xc0000000/268435456, 0xd6000000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    28.692] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.692] (II) "extmod" will be loaded by default.
[    28.692] (II) "dbe" will be loaded by default.
[    28.692] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    28.692] (II) "record" will be loaded by default.
[    28.692] (II) "dri" will be loaded by default.
[    28.692] (II) "dri2" will be loaded by default.
[    28.692] (II) LoadModule: "glx"
[    28.788] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    28.889] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    28.889]    compiled for 6.9.0, module version = 1.0.0
[    28.889] (II) Loading extension GLX
[    28.889] (II) LoadModule: "extmod"
[    29.056] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.120] (II) Module extmod: vendor="X.Org Foundation"
[    29.120]    compiled for 1.11.3, module version = 1.0.0
[    29.120]    Module class: X.Org Server Extension
[    29.120]    ABI class: X.Org Server Extension, version 6.0
[    29.120] (II) Loading extension MIT-SCREEN-SAVER
[    29.120] (II) Loading extension XFree86-VidModeExtension
[    29.120] (II) Loading extension XFree86-DGA
[    29.142] (II) Loading extension DPMS
[    29.142] (II) Loading extension XVideo
[    29.142] (II) Loading extension XVideo-MotionCompensation
[    29.142] (II) Loading extension X-Resource
[    29.142] (II) LoadModule: "dbe"
[    29.142] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.188] (II) Module dbe: vendor="X.Org Foundation"
[    29.188]    compiled for 1.11.3, module version = 1.0.0
[    29.188]    Module class: X.Org Server Extension
[    29.188]    ABI class: X.Org Server Extension, version 6.0
[    29.188] (II) Loading extension DOUBLE-BUFFER
[    29.188] (II) LoadModule: "record"
[    29.188] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.214] (II) Module record: vendor="X.Org Foundation"
[    29.214]    compiled for 1.11.3, module version = 1.13.0
[    29.214]    Module class: X.Org Server Extension
[    29.214]    ABI class: X.Org Server Extension, version 6.0
[    29.214] (II) Loading extension RECORD
[    29.214] (II) LoadModule: "dri"
[    29.214] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.254] (II) Module dri: vendor="X.Org Foundation"
[    29.255]    compiled for 1.11.3, module version = 1.0.0
[    29.255]    ABI class: X.Org Server Extension, version 6.0
[    29.255] (II) Loading extension XFree86-DRI
[    29.255] (II) LoadModule: "dri2"
[    29.255] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.255] (II) Module dri2: vendor="X.Org Foundation"
[    29.255]    compiled for 1.11.3, module version = 1.2.0
[    29.255]    ABI class: X.Org Server Extension, version 6.0
[    29.255] (II) Loading extension DRI2
[    29.255] (II) LoadModule: "fglrx"
[    29.255] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    30.155] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    30.187]    compiled for 1.4.99.906, module version = 8.96.4
[    30.187]    Module class: X.Org Video Driver
[    30.204] (II) Loading sub module "fglrxdrm"
[    30.204] (II) LoadModule: "fglrxdrm"
[    30.204] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    30.309] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    30.309]    compiled for 1.4.99.906, module version = 8.96.4
[    30.312] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    30.312] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[    30.312] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:47
[    30.312] (++) using VT number 7

[    30.312] (WW) Falling back to old probe method for fglrx
[    30.603] (II) Loading PCS database from /etc/ati/amdpcsdb
[    30.765] (--) Chipset Supported AMD Graphics Processor (0x68C1) found
[    30.765] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    30.766] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    30.805] (II) AMD Video driver is signed
[    30.805] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    30.805] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    30.805] (II) fglrx(0): pEnt->device->identifier=0xb86c7628
[    30.805] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    30.805] (II) Loading sub module "vgahw"
[    30.805] (II) LoadModule: "vgahw"
[    30.806] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    30.839] (II) Module vgahw: vendor="X.Org Foundation"
[    30.839]    compiled for 1.11.3, module version = 0.1.0
[    30.839]    ABI class: X.Org Video Driver, version 11.0
[    30.840] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    30.840] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    30.840] (==) fglrx(0): Default visual is TrueColor
[    30.840] (==) fglrx(0): RGB weight 888
[    30.840] (II) fglrx(0): Using 8 bits per RGB 
[    30.840] (==) fglrx(0): Buffer Tiling is ON
[    30.864] (II) Loading sub module "fglrxdrm"
[    30.864] (II) LoadModule: "fglrxdrm"
[    30.865] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    30.865] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    30.865]    compiled for 1.4.99.906, module version = 8.96.4
[    30.866] ukiDynamicMajor: found major device number 249
[    30.867] ukiDynamicMajor: found major device number 249
[    30.867] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    30.867] ukiOpenDevice: node name is /dev/ati/card0
[    30.867] ukiOpenDevice: open result is 12, (OK)
[    30.867] ukiOpenByBusid: ukiOpenMinor returns 12
[    30.867] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    30.867] (**) fglrx(0): NoAccel = NO
[    30.867] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    30.867] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 5000 Series " (Chipset = 0x68c1)
[    30.867] (--) fglrx(0): (PciSubVendor = 0x1179, PciSubDevice = 0xfd12)
[    30.867] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    30.867] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    30.867] (--) fglrx(0): MMIO registers at 0xd6000000
[    30.867] (--) fglrx(0): I/O port at 0x00004000
[    30.867] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    30.897] (II) fglrx(0): AC Adapter is used
[    31.105] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    31.141] (II) Loading sub module "vbe"
[    31.141] (II) LoadModule: "vbe"
[    31.142] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    31.217] (II) Module vbe: vendor="X.Org Foundation"
[    31.217]    compiled for 1.11.3, module version = 1.1.0
[    31.217]    ABI class: X.Org Video Driver, version 11.0
[    31.218] (II) fglrx(0): VESA BIOS detected
[    31.218] (II) fglrx(0): VESA VBE Version 3.0
[    31.218] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    31.218] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    31.218] (II) fglrx(0): VESA VBE OEM Software Rev: 12.19
[    31.218] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    31.218] (II) fglrx(0): VESA VBE OEM Product: MADISON
[    31.218] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    31.253] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    31.253] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    31.253] (II) fglrx(0): PCIE card detected
[    31.253] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    31.253] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    31.263] (II) fglrx(0): Using adapter: 1:0.0.
[    31.302] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    31.845] (II) fglrx(0): Interrupt handler installed at IRQ 46.
[    31.845] (II) fglrx(0): RandR 1.2 support is enabled!
[    31.845] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    31.845] (==) fglrx(0): Center Mode is disabled 
[    31.845] (II) Loading sub module "fb"
[    31.845] (II) LoadModule: "fb"
[    31.845] (II) Loading /usr/lib/xorg/modules/libfb.so
[    31.980] (II) Module fb: vendor="X.Org Foundation"
[    31.980]    compiled for 1.11.3, module version = 1.0.0
[    31.980]    ABI class: X.Org ANSI C Emulation, version 0.4
[    31.980] (II) Loading sub module "ddc"
[    31.980] (II) LoadModule: "ddc"
[    31.980] (II) Module "ddc" already built-in
[    32.491] (II) fglrx(0): Finished Initialize PPLIB!
[    32.497] (II) fglrx(0): Output LVDS using monitor section 0-LVDS
[    32.497] (**) fglrx(0): Option "PreferredMode" "1366x768"
[    32.497] (**) fglrx(0): Option "Position" "1280 0"
[    32.497] (**) fglrx(0): Option "Disable" "false"
[    32.497] (**) fglrx(0): Option "Rotate" "normal"
[    32.497] (**) fglrx(0): Option "TargetRefresh" "60"
[    32.497] (II) fglrx(0): Output DFP1 has no monitor section
[    32.497] (II) fglrx(0): Output CRT1 using monitor section 0-CRT1
[    32.497] (**) fglrx(0): Option "PreferredMode" "1280x1024"
[    32.497] (**) fglrx(0): Option "Position" "0 0"
[    32.497] (**) fglrx(0): Option "Disable" "false"
[    32.497] (**) fglrx(0): Option "Rotate" "normal"
[    32.497] (**) fglrx(0): Option "TargetRefresh" "60"
[    32.497] (II) Loading sub module "ddc"
[    32.497] (II) LoadModule: "ddc"
[    32.497] (II) Module "ddc" already built-in
[    32.497] (II) fglrx(0): Connected Display0: LVDS
[    32.497] (II) fglrx(0): Display0 EDID data ---------------------------
[    32.497] (II) fglrx(0): Manufacturer: LGD  Model: 26c  Serial#: 0
[    32.497] (II) fglrx(0): Year: 2010  Week: 0
[    32.497] (II) fglrx(0): EDID Version: 1.3
[    32.497] (II) fglrx(0): Digital Display Input
[    32.497] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    32.497] (II) fglrx(0): Gamma: 2.20
[    32.497] (II) fglrx(0): No DPMS capabilities specified
[    32.497] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    32.497] (II) fglrx(0): First detailed timing is preferred mode
[    32.497] (II) fglrx(0): redX: 0.622 redY: 0.365   greenX: 0.340 greenY: 0.607
[    32.497] (II) fglrx(0): blueX: 0.145 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    32.497] (II) fglrx(0): Manufacturer's mask: 0
[    32.497] (II) fglrx(0): Supported detailed timing:
[    32.497] (II) fglrx(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[    32.497] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    32.497] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    32.497] (II) fglrx(0):  LG Display
[    32.497] (II) fglrx(0):  LP156WH2-TLBA
[    32.497] (II) fglrx(0): EDID (in hex):
[    32.498] (II) fglrx(0):     00ffffffffffff0030e46c0200000000
[    32.498] (II) fglrx(0):     00140103802313780a62259f5d579b25
[    32.498] (II) fglrx(0):     19505400000001010101010101010101
[    32.498] (II) fglrx(0):     0101010101013e1c56a0500016303020
[    32.498] (II) fglrx(0):     350059c2100000190000000000000000
[    32.498] (II) fglrx(0):     00000000000000000000000000fe004c
[    32.498] (II) fglrx(0):     4720446973706c61790a2020000000fe
[    32.498] (II) fglrx(0):     004c503135365748322d544c424100f6
[    32.498] (II) fglrx(0): End of Display0 EDID data --------------------
[    32.498] (II) fglrx(0): EDID for output LVDS
[    32.498] (II) fglrx(0): Manufacturer: LGD  Model: 26c  Serial#: 0
[    32.498] (II) fglrx(0): Year: 2010  Week: 0
[    32.498] (II) fglrx(0): EDID Version: 1.3
[    32.498] (II) fglrx(0): Digital Display Input
[    32.498] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    32.498] (II) fglrx(0): Gamma: 2.20
[    32.498] (II) fglrx(0): No DPMS capabilities specified
[    32.498] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    32.498] (II) fglrx(0): First detailed timing is preferred mode
[    32.498] (II) fglrx(0): redX: 0.622 redY: 0.365   greenX: 0.340 greenY: 0.607
[    32.498] (II) fglrx(0): blueX: 0.145 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    32.498] (II) fglrx(0): Manufacturer's mask: 0
[    32.498] (II) fglrx(0): Supported detailed timing:
[    32.498] (II) fglrx(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[    32.498] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    32.498] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    32.498] (II) fglrx(0):  LG Display
[    32.498] (II) fglrx(0):  LP156WH2-TLBA
[    32.498] (II) fglrx(0): EDID (in hex):
[    32.498] (II) fglrx(0):     00ffffffffffff0030e46c0200000000
[    32.498] (II) fglrx(0):     00140103802313780a62259f5d579b25
[    32.498] (II) fglrx(0):     19505400000001010101010101010101
[    32.498] (II) fglrx(0):     0101010101013e1c56a0500016303020
[    32.498] (II) fglrx(0):     350059c2100000190000000000000000
[    32.498] (II) fglrx(0):     00000000000000000000000000fe004c
[    32.498] (II) fglrx(0):     4720446973706c61790a2020000000fe
[    32.499] (II) fglrx(0):     004c503135365748322d544c424100f6
[    32.499] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    32.499] (II) fglrx(0): Printing DDC gathered Modelines:
[    32.499] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Printing probed modes for output LVDS
[    32.499] (II) fglrx(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Modeline "1360x768"x60.0   72.30  1360 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Modeline "1280x768"x60.0   72.30  1280 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Modeline "1280x720"x60.0   72.30  1280 1414 1446 1526  720 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Modeline "1024x768"x60.0   72.30  1024 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Modeline "1024x600"x60.0   72.30  1024 1414 1446 1526  600 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Modeline "800x600"x60.0   72.30  800 1414 1446 1526  600 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Modeline "800x480"x60.0   72.30  800 1414 1446 1526  480 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): Modeline "640x480"x60.0   72.30  640 1414 1446 1526  480 771 776 790 -hsync -vsync (47.4 kHz)
[    32.499] (II) fglrx(0): EDID for output DFP1
[    32.499] (II) fglrx(0): EDID for output CRT1
[    32.499] (II) fglrx(0): Output LVDS connected
[    32.499] (II) fglrx(0): Output DFP1 disconnected
[    32.499] (II) fglrx(0): Output CRT1 disconnected
[    32.499] (II) fglrx(0): Using user preference for initial modes
[    32.499] (II) fglrx(0): Output LVDS using initial mode 1366x768
[    32.499] (II) fglrx(0): Display dimensions: (350, 190) mm
[    32.499] (II) fglrx(0): DPI set to (99, 102)
[    32.499] (II) fglrx(0): Eyefinity capable adapter detected.
[    32.499] (II) fglrx(0): Adapter ATI Mobility Radeon HD 5000 Series  has 6 configurable heads and 1 displays connected.
[    32.499] (==) fglrx(0):  PseudoColor visuals disabled
[    32.499] (II) Loading sub module "ramdac"
[    32.499] (II) LoadModule: "ramdac"
[    32.499] (II) Module "ramdac" already built-in
[    32.499] (==) fglrx(0): NoDRI = NO
[    32.499] (==) fglrx(0): Capabilities: 0x00000000
[    32.499] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    32.499] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    32.499] (==) fglrx(0): UseFastTLS=0
[    32.499] (==) fglrx(0): BlockSignalsOnLock=1
[    32.499] (--) Depth 24 pixmap format is 32 bpp
[    32.499] (II) Loading extension ATIFGLRXDRI
[    32.499] (II) fglrx(0): doing swlDriScreenInit
[    32.499] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    32.499] ukiDynamicMajor: found major device number 249
[    32.499] ukiDynamicMajor: found major device number 249
[    32.500] ukiDynamicMajor: found major device number 249
[    32.500] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    32.500] ukiOpenDevice: node name is /dev/ati/card0
[    32.500] ukiOpenDevice: open result is 17, (OK)
[    32.500] ukiOpenByBusid: ukiOpenMinor returns 17
[    32.500] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    32.500] (II) fglrx(0): [uki] DRM interface version 1.0
[    32.500] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    32.500] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    32.500] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb6f2a000
[    32.500] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    32.500] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    32.500] (II) fglrx(0): swlDriScreenInit done
[    32.500] (II) fglrx(0): Kernel Module Version Information:
[    32.500] (II) fglrx(0):     Name: fglrx
[    32.500] (II) fglrx(0):     Version: 8.96.4
[    32.500] (II) fglrx(0):     Date: Mar 12 2012
[    32.500] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    32.500] (II) fglrx(0): Kernel Module version matches driver.
[    32.500] (II) fglrx(0): Kernel Module Build Time Information:
[    32.500] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-24-generic-pae
[    32.500] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    32.500] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    32.500] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    32.500] (II) fglrx(0): [uki] register handle = 0x00004000
[    32.573] (II) fglrx(0): DRI initialization successfull
[    32.586] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01b90000
[    32.608] (==) fglrx(0): Backing store disabled
[    32.608] (II) Loading extension FGLRXEXTENSION
[    32.608] (==) fglrx(0): DPMS enabled
[    32.608] (II) fglrx(0): Initialized in-driver Xinerama extension
[    32.608] (**) fglrx(0): Textured Video is enabled.
[    32.608] (II) LoadModule: "glesx"
[    32.608] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    33.189] (II) Module glesx: vendor="X.Org Foundation"
[    33.189]    compiled for 1.4.99.906, module version = 1.0.0
[    33.189] (II) Loading extension GLESX
[    33.189] (II) fglrx(0): GLESX enableFlags = 592
[    33.198] (II) fglrx(0): GLESX is enabled
[    33.198] (II) LoadModule: "amdxmm"
[    33.199] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    33.237] (II) Module amdxmm: vendor="X.Org Foundation"
[    33.237]    compiled for 1.4.99.906, module version = 2.0.0
[    33.245] (II) Loading extension AMDXVOPL
[    33.245] (II) Loading extension AMDXVBA
[    33.270] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    33.383] (II) fglrx(0): Enable composite support successfully
[    33.384] (II) fglrx(0): X context handle = 0x1
[    33.384] (II) fglrx(0): [DRI] installation complete
[    33.384] (==) fglrx(0): Silken mouse enabled
[    33.384] (==) fglrx(0): Using HW cursor of display infrastructure!
[    33.385] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    33.385] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    33.385] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    33.396] (II) fglrx(0): User Preference Output LVDS using refresh rate 60.0 Hz.
[    34.358] (--) RandR disabled
[    34.358] (II) Initializing built-in extension Generic Event Extension
[    34.358] (II) Initializing built-in extension SHAPE
[    34.358] (II) Initializing built-in extension MIT-SHM
[    34.358] (II) Initializing built-in extension XInputExtension
[    34.358] (II) Initializing built-in extension XTEST
[    34.358] (II) Initializing built-in extension BIG-REQUESTS
[    34.358] (II) Initializing built-in extension SYNC
[    34.358] (II) Initializing built-in extension XKEYBOARD
[    34.358] (II) Initializing built-in extension XC-MISC
[    34.358] (II) Initializing built-in extension SECURITY
[    34.358] (II) Initializing built-in extension XINERAMA
[    34.358] (II) Initializing built-in extension XFIXES
[    34.358] (II) Initializing built-in extension RENDER
[    34.358] (II) Initializing built-in extension RANDR
[    34.358] (II) Initializing built-in extension COMPOSITE
[    34.358] (II) Initializing built-in extension DAMAGE
[    34.398] ukiDynamicMajor: found major device number 249
[    34.398] ukiDynamicMajor: found major device number 249
[    34.398] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    34.398] ukiOpenDevice: node name is /dev/ati/card0
[    34.398] ukiOpenDevice: open result is 19, (OK)
[    34.398] ukiOpenByBusid: ukiOpenMinor returns 19
[    34.398] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    35.144] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    35.144] (II) fglrx(0): Enable the clock gating!
[    35.144] (II) fglrx(0): Setting screen physical size to 700 x 203
[    35.296] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    35.316] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    35.316] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.316] (II) LoadModule: "evdev"
[    35.317] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.350] (II) Module evdev: vendor="X.Org Foundation"
[    35.350]    compiled for 1.11.3, module version = 2.7.0
[    35.351]    Module class: X.Org XInput Driver
[    35.351]    ABI class: X.Org XInput driver, version 16.0
[    35.351] (II) Using input driver 'evdev' for 'Power Button'
[    35.351] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.351] (**) Power Button: always reports core events
[    35.351] (**) evdev: Power Button: Device: "/dev/input/event2"
[    35.351] (--) evdev: Power Button: Vendor 0 Product 0x1
[    35.351] (--) evdev: Power Button: Found keys
[    35.351] (II) evdev: Power Button: Configuring as keyboard
[    35.351] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    35.351] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    35.351] (**) Option "xkb_rules" "evdev"
[    35.351] (**) Option "xkb_model" "pc105"
[    35.351] (**) Option "xkb_layout" "de"
[    35.353] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    35.355] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    35.355] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    35.356] (II) Using input driver 'evdev' for 'Video Bus'
[    35.356] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.356] (**) Video Bus: always reports core events
[    35.356] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    35.356] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    35.356] (--) evdev: Video Bus: Found keys
[    35.356] (II) evdev: Video Bus: Configuring as keyboard
[    35.356] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4/event4"
[    35.356] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    35.356] (**) Option "xkb_rules" "evdev"
[    35.356] (**) Option "xkb_model" "pc105"
[    35.356] (**) Option "xkb_layout" "de"
[    35.356] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    35.356] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.356] (II) Using input driver 'evdev' for 'Power Button'
[    35.356] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.356] (**) Power Button: always reports core events
[    35.356] (**) evdev: Power Button: Device: "/dev/input/event0"
[    35.356] (--) evdev: Power Button: Vendor 0 Product 0x1
[    35.356] (--) evdev: Power Button: Found keys
[    35.356] (II) evdev: Power Button: Configuring as keyboard
[    35.356] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/PNP0C0C:00/input/input0/event0"
[    35.356] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    35.356] (**) Option "xkb_rules" "evdev"
[    35.356] (**) Option "xkb_model" "pc105"
[    35.356] (**) Option "xkb_layout" "de"
[    35.357] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    35.357] (II) No input driver specified, ignoring this device.
[    35.357] (II) This device may have been added with another device file.
[    35.357] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event9)
[    35.357] (II) No input driver specified, ignoring this device.
[    35.357] (II) This device may have been added with another device file.
[    35.358] (II) config/udev: Adding input device USB Camera (/dev/input/event7)
[    35.358] (**) USB Camera: Applying InputClass "evdev keyboard catchall"
[    35.358] (II) Using input driver 'evdev' for 'USB Camera'
[    35.358] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.358] (**) USB Camera: always reports core events
[    35.358] (**) evdev: USB Camera: Device: "/dev/input/event7"
[    35.358] (--) evdev: USB Camera: Vendor 0x10f1 Product 0x1a2a
[    35.358] (--) evdev: USB Camera: Found keys
[    35.358] (II) evdev: USB Camera: Configuring as keyboard
[    35.358] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input7/event7"
[    35.358] (II) XINPUT: Adding extended input device "USB Camera" (type: KEYBOARD, id 9)
[    35.358] (**) Option "xkb_rules" "evdev"
[    35.358] (**) Option "xkb_model" "pc105"
[    35.358] (**) Option "xkb_layout" "de"
[    35.358] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1017 (/dev/input/event6)
[    35.358] (**) Logitech Unifying Device. Wireless PID:1017: Applying InputClass "evdev pointer catchall"
[    35.358] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1017'
[    35.358] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.358] (**) Logitech Unifying Device. Wireless PID:1017: always reports core events
[    35.358] (**) evdev: Logitech Unifying Device. Wireless PID:1017: Device: "/dev/input/event6"
[    35.358] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Vendor 0x46d Product 0xc52b
[    35.358] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Found 20 mouse buttons
[    35.358] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Found scroll wheel(s)
[    35.358] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Found relative axes
[    35.358] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Found x and y relative axes
[    35.358] (II) evdev: Logitech Unifying Device. Wireless PID:1017: Configuring as mouse
[    35.358] (II) evdev: Logitech Unifying Device. Wireless PID:1017: Adding scrollwheel support
[    35.358] (**) evdev: Logitech Unifying Device. Wireless PID:1017: YAxisMapping: buttons 4 and 5
[    35.358] (**) evdev: Logitech Unifying Device. Wireless PID:1017: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.358] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.2/0003:046D:C52B.0003/input/input6/event6"
[    35.359] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1017" (type: MOUSE, id 10)
[    35.359] (II) evdev: Logitech Unifying Device. Wireless PID:1017: initialized for relative axes.
[    35.359] (**) Logitech Unifying Device. Wireless PID:1017: (accel) keeping acceleration scheme 1
[    35.359] (**) Logitech Unifying Device. Wireless PID:1017: (accel) acceleration profile 0
[    35.359] (**) Logitech Unifying Device. Wireless PID:1017: (accel) acceleration factor: 2.000
[    35.359] (**) Logitech Unifying Device. Wireless PID:1017: (accel) acceleration threshold: 4
[    35.359] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1017 (/dev/input/mouse0)
[    35.359] (II) No input driver specified, ignoring this device.
[    35.359] (II) This device may have been added with another device file.
[    35.359] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    35.359] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    35.359] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    35.359] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.359] (**) AT Translated Set 2 keyboard: always reports core events
[    35.359] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    35.359] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    35.359] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    35.359] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    35.359] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    35.359] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    35.359] (**) Option "xkb_rules" "evdev"
[    35.359] (**) Option "xkb_model" "pc105"
[    35.359] (**) Option "xkb_layout" "de"
[    35.360] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    35.360] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    35.360] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    35.360] (II) LoadModule: "synaptics"
[    35.360] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    35.374] (II) Module synaptics: vendor="X.Org Foundation"
[    35.374]    compiled for 1.11.3, module version = 1.6.0
[    35.374]    Module class: X.Org XInput Driver
[    35.374]    ABI class: X.Org XInput driver, version 16.0
[    35.374] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    35.374] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    35.374] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    35.374] (**) Option "Device" "/dev/input/event8"
[    35.388] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    35.388] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[    35.388] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[    35.388] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    35.388] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    35.388] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    35.388] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    35.388] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    35.388] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    35.392] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    35.392] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    35.392] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    35.392] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    35.392] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    35.392] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    35.392] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    35.392] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    35.392] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    35.392] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    35.392] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    35.392] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    35.394] (II) config/udev: Adding input device Toshiba input device (/dev/input/event5)
[    35.394] (**) Toshiba input device: Applying InputClass "evdev keyboard catchall"
[    35.394] (II) Using input driver 'evdev' for 'Toshiba input device'
[    35.394] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.394] (**) Toshiba input device: always reports core events
[    35.394] (**) evdev: Toshiba input device: Device: "/dev/input/event5"
[    35.394] (--) evdev: Toshiba input device: Vendor 0 Product 0
[    35.394] (--) evdev: Toshiba input device: Found keys
[    35.394] (II) evdev: Toshiba input device: Configuring as keyboard
[    35.394] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    35.394] (II) XINPUT: Adding extended input device "Toshiba input device" (type: KEYBOARD, id 13)
[    35.394] (**) Option "xkb_rules" "evdev"
[    35.394] (**) Option "xkb_model" "pc105"
[    35.394] (**) Option "xkb_layout" "de"
[    35.398] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    35.415] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    35.415] (II) fglrx(0): Printing DDC gathered Modelines:
[    35.415] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    38.176] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    38.177] (II) fglrx(0): Printing DDC gathered Modelines:
[    38.177] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    40.634] (II) fglrx(0): xdl_xs111_atiddxDisplayScreenEnableDisplays
[    48.263] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    48.264] (II) fglrx(0): Printing DDC gathered Modelines:
[    48.264] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    52.682] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    52.682] (II) fglrx(0): Printing DDC gathered Modelines:
[    52.682] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    52.692] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    52.692] (II) fglrx(0): Printing DDC gathered Modelines:
[    52.692] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    52.702] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    52.702] (II) fglrx(0): Printing DDC gathered Modelines:
[    52.702] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    62.167] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    62.167] (II) fglrx(0): Printing DDC gathered Modelines:
[    62.167] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    85.418] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    85.434] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    85.437] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    85.439] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    85.442] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    85.444] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    95.331] (II) fglrx(0): EDID vendor "LGD", prod id 620
[    95.331] (II) fglrx(0): Printing DDC gathered Modelines:
[    95.331] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   161.780] (II) AIGLX: Suspending AIGLX clients for VT switch
[   161.784] (II) fglrx(0): Backup framebuffer data.
[   161.825] (II) fglrx(0): Backup complete.
[   161.853] (EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
[   161.853] (EE) fglrx(0):        ulEventType = 00000023, ulEventData = 00000001
[   165.204] (II) AIGLX: Resuming AIGLX clients after VT switch
[   165.246] (II) fglrx(0): User Preference Output LVDS using refresh rate 60.0 Hz.
[   166.233] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   172.360] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   172.363] (II) fglrx(0): Printing DDC gathered Modelines:
[   172.363] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   179.599] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   179.599] (II) fglrx(0): Printing DDC gathered Modelines:
[   179.599] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   180.019] (II) fglrx(0): xdl_xs111_atiddxDisplayScreenEnableDisplays
[   180.642] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   180.642] (II) fglrx(0): Printing DDC gathered Modelines:
[   180.642] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   180.655] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   180.655] (II) fglrx(0): Printing DDC gathered Modelines:
[   180.655] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   180.664] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   180.664] (II) fglrx(0): Printing DDC gathered Modelines:
[   180.664] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   180.736] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   180.736] (II) fglrx(0): Printing DDC gathered Modelines:
[   180.736] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   181.048] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   181.048] (II) fglrx(0): Printing DDC gathered Modelines:
[   181.048] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   181.058] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   181.058] (II) fglrx(0): Printing DDC gathered Modelines:
[   181.058] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   181.105] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   181.105] (II) fglrx(0): Printing DDC gathered Modelines:
[   181.105] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   181.120] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   181.120] (II) fglrx(0): Printing DDC gathered Modelines:
[   181.120] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   186.669] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   186.669] (II) fglrx(0): Printing DDC gathered Modelines:
[   186.669] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   187.085] (II) fglrx(0): xdl_xs111_atiddxDisplayScreenEnableDisplays
[   187.719] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   187.719] (II) fglrx(0): Printing DDC gathered Modelines:
[   187.719] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   187.732] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   187.732] (II) fglrx(0): Printing DDC gathered Modelines:
[   187.732] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   187.741] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   187.741] (II) fglrx(0): Printing DDC gathered Modelines:
[   187.741] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   187.829] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   187.829] (II) fglrx(0): Printing DDC gathered Modelines:
[   187.829] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   188.190] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   188.190] (II) fglrx(0): Printing DDC gathered Modelines:
[   188.190] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   188.203] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   188.203] (II) fglrx(0): Printing DDC gathered Modelines:
[   188.203] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   188.212] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   188.212] (II) fglrx(0): Printing DDC gathered Modelines:
[   188.212] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   188.248] (II) fglrx(0): EDID vendor "LGD", prod id 620
[   188.248] (II) fglrx(0): Printing DDC gathered Modelines:
[   188.248] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)

```

---

### Post by athlon2000 on 2012-05-28
Hello again,

I just executed the following line in the terminal:
$ sudo dpkg-reconfigure -phigh xserver-xorg

and now it seems to be behave normal again.
The only strange thing I experience now when I come back from the console mode is that the mouse cursor looks like dotted "rail tracks". Funny enough, when I take a screenshot of the cursor it looks normal on the picture. But I guess I can live with that.

EDIT: I'm not sure if the reconfigure command was really help full, because I just read this is outdated and does nothing. The other thing I did before it worked was that I executed the xrandr -o left command before I switched to the console and when I came back the window was still normal. Then I just had to execute the xrandr -o normal command and since then it works as described above.

---

