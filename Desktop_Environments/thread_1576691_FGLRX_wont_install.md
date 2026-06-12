---
title: "FGLRX wont install"
date: 2010-09-17
forum: Desktop Environments
---

### Post by mickmouse13 on 2010-09-17
I updated this morning (not from version to version) just a normal upgrade like one would do every morning. And i think fglrx failed. I did not notice at the time but a few things were amiss and eventually i noticed compositing was turned off, then i found out System>Admin>Drivers Said my driver was off. I tried to re enable it and got nowhere. So through a ton of troubleshooting and googling this is where I'm at now. so i apt-get install fglrx, and get this output.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fglrx (2:8.771-0ubuntu0sarvatt~lucid) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-8.771 DKMS files...

------------------------------
Deleting module version: 8.771
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.771 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture x86_64
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                       Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)
```and this popped up in another window
```
E: fglrx: subprocess installed post-installation script returned error exit status 10
E: fglrx-amdcccle: dependency problems - leaving unconfigured
```I have done anything and everything from uninstalling,purging,deleting the /usr/share/ati folder, its getting a bit odd. I figure there is just a file somewhere i cant find to delete and that is causing problems for install... Anyone who knows let me know thanks!

I am in ubuntu 10.04

Some more info is that now going to HardwareDrivers, there is nothing shown. My screen resolutions has also lowered since the last reboot, and going to "Monitors" Returns 
```
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
```I click yes and get 
```
 p, li { white-space: pre-wrap; } There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 
 No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
```

---

### Post by TwelveGauge on 2010-09-17
assuming you're running an Radeon HD XXXX card and not like a x???? series card then what might work is to remove everything related to AIT, update and then enable the propritary driver when it pops up. I had a very similar problem with my computer and my Radeon HD 46whatever. I did this more or less when i ran out of other ideas and it seems to have worked. 

To be perfictly honest the ATI drivers cause untold numbers of problems that all manifest in different ways.

If you're not using an HD Radeon card then the ATI drivers are not supported and will not run.

---

### Post by mickmouse13 on 2010-09-17
I posted the log mentioned in one of the errors, and i will now try what previous posted said.

---

### Post by mickmouse13 on 2010-09-17
[TwelveGauge]("http://ubuntuforums.org/member.php?u=1127440")'s idea did not do much, i removed fglrx-radeon and other packages that apeared with "fglrx" and "ati" (besides jocky) And still nothing new.

---

### Post by mickmouse13 on 2010-09-17
running lspci i figured out this is my grafics card 
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobili
ty Radeon HD 4650]
Hope it helps.

---

### Post by TwelveGauge on 2010-09-17
nvm >_>

and i'm sorry it didn't work for you....but did you reenable the ati drivers?

---

### Post by mickmouse13 on 2010-09-17
Yep. I have catalyst controle center, and my resolution works again. but if i go to system>admin>hardwaredrivers It is still blank. And desktop effectts are still not usable.
I also tried to reinstall "xserver-xorg-video-radeon" And it went fine till it hit the "configuring fglrx" And then failed the same way it all is.

---

### Post by mickmouse13 on 2010-09-17
I dont meant to keep bumping.. but i keep finding new things. 
This is what i get if i cat /var/log/xorg.0.log

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kenshin133-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=b9d5df73-c91b-4ef6-8f55-5537ff9c6955 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 17 18:33:41 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:9480:104d:9035 ATI Technologies Inc M96 [Mobility Radeon HD 4650] rev 0, Mem @ 0xc0000000/268435456, 0xd0020000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.77.5
    Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.77.5
(II) ATI Proprietary Linux Driver Version Identifier:8.77.5
(II) ATI Proprietary Linux Driver Release Identifier: 8.771                                
(II) ATI Proprietary Linux Driver Build Date: Aug 25 2010 21:38:26
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9480) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0xc68a20
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: failed to open /proc/ati/major
ukiDynamicMajor: failed to open /proc/ati/major
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): ATI 2D Acceleration Architecture enabled
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4650" (Chipset = 0x9480)
(--) fglrx(0): (PciSubVendor = 0x104d, PciSubDevice = 0x9035)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xd0020000
(--) fglrx(0): I/O port at 0x0000d000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(EE) fglrx(0): ACPI: DRM connection failed
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 11.22
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M96
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 524288 kByte, Type: GDDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): ACPI: DRM connection failed
(WW) fglrx(0): Hasn't establisted DRM connection
(II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) fglrx(0): Active stereo disabled
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output DFP1 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: LVDS
(II) fglrx(0):  Display0: Failed to get EDID information. 
(II) fglrx(0): Cannot get EDID information for LVDS
(II) fglrx(0): Output LVDS connected
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output LVDS using initial mode 1600x900
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Mobility Radeon HD 4650 has 2 configurable heads and 1 displays connected.
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************************
(WW) fglrx(0): * DRI initialization failed                               *
(WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
(WW) fglrx(0): * 2D and 3D acceleration disabled                         *
(WW) fglrx(0): ***********************************************************
(II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1600) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 6591
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 512
(II) fglrx(0): Acceleration enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(EE) fglrx(0): XMM failed to open CMMQS connection.
(EE) fglrx(0): XMM failed to initialize
(WW) fglrx(0): No XV video playback available
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
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
(II) AIGLX: Screen 0 is not DRI capable
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
(II) fglrx(0): Setting screen physical size to 423 x 238
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event7)
(**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event7"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device UVC Camera (05ca:183d) (/dev/input/event6)
(**) UVC Camera (05ca:183d): Applying InputClass "evdev keyboard catchall"
(**) UVC Camera (05ca:183d): always reports core events
(**) UVC Camera (05ca:183d): Device: "/dev/input/event6"
(II) UVC Camera (05ca:183d): Found keys
(II) UVC Camera (05ca:183d): Configuring as keyboard
(II) XINPUT: Adding extended input device "UVC Camera (05ca:183d)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HID 04b3:310b (/dev/input/event4)
(**) HID 04b3:310b: Applying InputClass "evdev pointer catchall"
(**) HID 04b3:310b: always reports core events
(**) HID 04b3:310b: Device: "/dev/input/event4"
(II) HID 04b3:310b: Found 3 mouse buttons
(II) HID 04b3:310b: Found scroll wheel(s)
(II) HID 04b3:310b: Found relative axes
(II) HID 04b3:310b: Found x and y relative axes
(II) HID 04b3:310b: Configuring as mouse
(**) HID 04b3:310b: YAxisMapping: buttons 4 and 5
(**) HID 04b3:310b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 04b3:310b" (type: MOUSE)
(II) HID 04b3:310b: initialized for relative axes.
(II) config/udev: Adding input device HID 04b3:310b (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event10)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event10"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event11)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event11"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(II) fglrx(0): Cannot get EDID information for LVDS
(II) fglrx(0): Cannot get EDID information for LVDS
(II) fglrx(0): Cannot get EDID information for LVDS
(II) fglrx(0): Cannot get EDID information for LVDS
(II) fglrx(0): Cannot get EDID information for LVDS
(II) fglrx(0): Cannot get EDID information for LVDS
(II) fglrx(0): Cannot get EDID information for LVDS

```

I dont know what im looking for, but someone in another thread found answers in there.

---

### Post by mickmouse13 on 2010-09-17
running fglrxinfo gives me a segmentation fault.

---

### Post by mickmouse13 on 2010-09-17
I'm gonna go the same route as everyone before me, just format, and reinstall.. Its sad because i dont think this was caused by me.. but thats life. Thanks for the help.

---

### Post by jtuchscherer on 2010-09-18
> **mickmouse13 said:**
> I'm gonna go the same route as everyone before me, just format, and reinstall.. Its sad because i dont think this was caused by me.. but thats life. Thanks for the help.

I have the same problem as of today. I normally use the ati driver from ati's web site. But after the kernal upgrade today, I cannot install it anymore. I am looking for the root cause right now.

This bug is the reason for my problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/640866](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/640866)
And here is a possible solution:
[http://phoronix.com/forums/showthread.php?t=25485](http://phoronix.com/forums/showthread.php?t=25485)

---

### Post by Matt G Dalian on 2010-09-18
I also have this problem after I updated my linux kernal using the update manager. Just yesterday I decided to finally activate my graphics card driver.

Interestingly, doing a google search for

*Error! Bad return status for module build on kernel: 2.6.32-24-generic (x86_64)*

yields ~10 bug reports from bugs.launchpad.net, many of which are from the last several days.

Fortunately, I have no major problems. But every time I try to install a package I get an error message (because apt is trying to clean up fglrx. The package still installs)

---

### Post by progre55_icky on 2010-09-19
I also stumbled upon the same problem today..
So what I ended up doing was:

1) removed the 32-24 kernel:
```
sudo apt-get remove --purge linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
```

2) removed the manually installed, but broken fglrx drivers:
```
sudo apt-get remove --purge fglrx fglrx-amdcccle fglrx-dev
```

3) installed the old kernel:
```
sudo apt-get install linux-headers-2.6.32-23 linux-headers-2.6.32-23-generic
```

4) installed fglrx from the repos (which installed with no problem on 32-23):
```
sudo apt-get install fglrx fglrx-amdcccle fglrx-dev
```

5) and finally, activated the proprietary drivers from "hardware drivers" and rebooted

This works fine, but not under 32-24, cause as soon as I install linux-headers-2.6.32-24 and boot into it, the proprietary drivers get broken again. So I guess I'll just have to wait until they fix the compilation bug under 32-24

Hope it helps.

Regards,
progre55

---

### Post by Captain Giraffe on 2010-09-19
Another fix for this is in [http://ww.ubuntuforums.org/showthread.php?p=9860156]("http://ww.ubuntuforums.org/showthread.php?p=9860156")

Don't miss sojous comments.

---

