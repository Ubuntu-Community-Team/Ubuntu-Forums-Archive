---
title: "XRDP close session just after login"
date: 2020-05-01
forum: Desktop Environments
---

### Post by WhiteTigerIT on 2020-05-01
I have to open an RDP session on a PC with Xubuntu.
I installed XRDP with the commands listed below.
When I try to connect with Remote Desktop from Windows 10 Pro, I am asked for the credentials of the PC, in the XRDP login panel.
But after the OK, after only a few seconds, the window closes and the connection panel returns in Windows.
Below there is also the log of **.xorgxrdp.10.log** and **xrdp-sesman.log**

Where am I doing wrong?

```
sudo apt-get install xrdp
sudo sed -i.bak '/fi/a #xrdp multiple users configuration \n xfce-session \n' /etc/xrdp/startwm.sh
sudo /etc/init.d/xrdp restart
```

```
[    81.852] X.Org X Server 1.20.8
X Protocol Version 11, Revision 0
[    81.852] Build Operating System: Linux 4.4.0-177-generic x86_64 Ubuntu
[    81.852] Current Operating System: Linux xubuntu-base 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64
[    81.852] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-28-generic root=UUID=01d72ecb-36fb-4096-a5cb-14d44da3b41f ro quiet splash
[    81.852] Build Date: 06 April 2020  09:39:29AM
[    81.852] xorg-server 2:1.20.8-2ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    81.852] Current version of pixman: 0.38.4
[    81.852] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    81.852] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    81.852] (++) Log file: ".xorgxrdp.10.log", Time: Sat May  2 10:53:18 2020
[    81.871] (++) Using config file: "/etc/X11/xrdp/xorg.conf"
[    81.871] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    81.872] (==) ServerLayout "X11 Server"
[    81.872] (**) |-->Screen "Screen (xrdpdev)" (0)
[    81.872] (**) |   |-->Monitor "Monitor"
[    81.873] (**) |   |-->Device "Video Card (xrdpdev)"
[    81.873] (**) |-->Input Device "xrdpMouse"
[    81.873] (**) |-->Input Device "xrdpKeyboard"
[    81.873] (**) Option "DontVTSwitch" "on"
[    81.873] (**) Option "AutoAddDevices" "off"
[    81.873] (**) Not automatically adding devices
[    81.873] (==) Automatically enabling devices
[    81.873] (==) Automatically adding GPU devices
[    81.873] (==) Automatically binding GPU devices
[    81.873] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    81.873] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    81.873] 	Entry deleted from font path.
[    81.873] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    81.873] 	Entry deleted from font path.
[    81.873] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    81.873] 	Entry deleted from font path.
[    81.873] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    81.873] 	Entry deleted from font path.
[    81.873] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    81.873] 	Entry deleted from font path.
[    81.873] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    81.873] (==) ModulePath set to "/usr/lib/xorg/modules"
[    81.873] (II) Loader magic: 0x56466ea34020
[    81.873] (II) Module ABI versions:
[    81.873] 	X.Org ANSI C Emulation: 0.4
[    81.873] 	X.Org Video Driver: 24.1
[    81.873] 	X.Org XInput driver : 24.1
[    81.873] 	X.Org Server Extension : 10.0
[    81.882] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c2
[    81.884] (II) xfree86: Adding drm device (/dev/dri/card0)
[    81.891] (EE) systemd-logind: failed to take device /dev/dri/card0: Operation not permitted
[    81.891] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
[    81.943] (--) PCI:*(0@0:15:0) 15ad:0405:15ad:0405 rev 0, Mem @ 0xe8000000/134217728, 0xfe000000/8388608, I/O @ 0x00001070/16, BIOS @ 0x????????/131072
[    81.943] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    81.943] (II) LoadModule: "dbe"
[    81.943] (II) Module "dbe" already built-in
[    81.943] (II) LoadModule: "ddc"
[    81.943] (II) Module "ddc" already built-in
[    81.943] (II) LoadModule: "extmod"
[    81.943] (II) Module "extmod" already built-in
[    81.943] (II) LoadModule: "glx"
[    81.943] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    81.964] (II) Module glx: vendor="X.Org Foundation"
[    81.967] 	compiled for 1.20.8, module version = 1.0.0
[    81.967] 	ABI class: X.Org Server Extension, version 10.0
[    81.967] (II) LoadModule: "int10"
[    81.968] (II) Loading /usr/lib/xorg/modules/libint10.so
[    81.987] (II) Module int10: vendor="X.Org Foundation"
[    81.987] 	compiled for 1.20.8, module version = 1.0.0
[    81.987] 	ABI class: X.Org Video Driver, version 24.1
[    81.987] (II) LoadModule: "record"
[    81.987] (II) Module "record" already built-in
[    81.987] (II) LoadModule: "vbe"
[    81.987] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    81.989] (II) Module vbe: vendor="X.Org Foundation"
[    81.989] 	compiled for 1.20.8, module version = 1.1.0
[    81.989] 	ABI class: X.Org Video Driver, version 24.1
[    81.989] (II) LoadModule: "glamoregl"
[    81.989] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    82.025] (II) Module glamoregl: vendor="X.Org Foundation"
[    82.026] 	compiled for 1.20.8, module version = 1.0.1
[    82.026] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    82.026] (II) LoadModule: "xorgxrdp"
[    82.026] (II) Loading /usr/lib/xorg/modules/libxorgxrdp.so
[    82.029] (II) Module XORGXRDP: vendor="X.Org Foundation"
[    82.029] 	compiled for 1.20.6, module version = 0.2.12
[    82.029] 	ABI class: X.Org Video Driver, version 24.0
[    82.029] xorgxrdpSetup:
[    82.029] (II) LoadModule: "fb"
[    82.029] (II) Loading /usr/lib/xorg/modules/libfb.so
[    82.029] (II) Module fb: vendor="X.Org Foundation"
[    82.029] 	compiled for 1.20.8, module version = 1.0.0
[    82.029] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    82.029] (II) LoadModule: "xrdpdev"
[    82.030] (II) Loading /usr/lib/xorg/modules/drivers/xrdpdev_drv.so
[    82.033] (II) Module XRDPDEV: vendor="X.Org Foundation"
[    82.033] 	compiled for 1.20.6, module version = 0.2.12
[    82.033] 	ABI class: X.Org Video Driver, version 24.0
[    82.034] xrdpdevSetup:
[    82.034] (II) LoadModule: "xrdpmouse"
[    82.034] (II) Loading /usr/lib/xorg/modules/input/xrdpmouse_drv.so
[    82.038] (II) Module XRDPMOUSE: vendor="X.Org Foundation"
[    82.038] 	compiled for 1.20.6, module version = 0.2.12
[    82.038] 	Module class: X.Org XInput Driver
[    82.038] 	ABI class: X.Org XInput driver, version 24.1
[    82.038] rdpmousePlug:
[    82.038] (II) LoadModule: "xrdpkeyb"
[    82.038] (II) Loading /usr/lib/xorg/modules/input/xrdpkeyb_drv.so
[    82.041] (II) Module XRDPKEYB: vendor="X.Org Foundation"
[    82.041] 	compiled for 1.20.6, module version = 0.2.12
[    82.041] 	Module class: X.Org XInput Driver
[    82.041] 	ABI class: X.Org XInput driver, version 24.1
[    82.041] rdpkeybPlug:
[    82.041] rdpIdentify:
[    82.041] (II) XRDPDEV: driver for xrdp: XRDPDEV
[    82.041] rdpDriverFunc: op 10
[    82.041] (WW) Falling back to old probe method for XRDPDEV
[    82.041] rdpProbe:
[    82.041] (II) Loading sub module "fb"
[    82.041] (II) LoadModule: "fb"
[    82.043] (II) Loading /usr/lib/xorg/modules/libfb.so
[    82.043] (II) Module fb: vendor="X.Org Foundation"
[    82.043] 	compiled for 1.20.8, module version = 1.0.0
[    82.043] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    82.043] rdpProbe: found DRMDevice xorg.conf value [/dev/dri/renderD128]
[    82.043] rdpProbe: found DRI3 xorg.conf value [1]
[    82.043] (II) XRDPDEV(0): using default device
[    82.043] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    82.043] rdpPreInit:
[    82.043] rdpPreInit: /dev/dri/renderD128 open ok, fd 10
[    82.043] (**) XRDPDEV(0): Depth 24, (--) framebuffer bpp 32
[    82.043] (==) XRDPDEV(0): RGB weight 888
[    82.043] (==) XRDPDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    82.043] (==) XRDPDEV(0): Default visual is TrueColor
[    82.043] (==) XRDPDEV(0): DPI set to (96, 96)
[    82.043] (II) XRDPDEV(0): 	mode "640x480" ok
[    82.043] (II) XRDPDEV(0): 	mode "800x600" ok
[    82.043] (II) XRDPDEV(0): Virtual size is 800x600 (pitch 800)
[    82.043] (**) XRDPDEV(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    82.043] (II) XRDPDEV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    82.043] (II) Loading sub module "glamoregl"
[    82.043] (II) LoadModule: "glamoregl"
[    82.043] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    82.043] (II) Module glamoregl: vendor="X.Org Foundation"
[    82.043] 	compiled for 1.20.8, module version = 1.0.1
[    82.043] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    82.043] rdpPreInit: glamor module load ok
[    82.183] (II) XRDPDEV(0): glamor X acceleration enabled on SVGA3D; build: RELEASE;  LLVM;
[    82.184] rdpPreInit: glamor init ok
[    82.184] rdpScreenInit: virtualX 800 virtualY 600 rgbBits 8 depth 24
[    82.184] rdpScreenInit: pfbMemory bytes 1920000
[    82.184] rdpScreenInit: pfbMemory 0x7f719c189010
[    82.184] rdpSimdInit: assigning yuv functions
[    82.184] rdpSimdInit: cpuid ax 1 cx 0 return ax 0x000306a9 bx 0x00010800 cx 0xbdba2203 dx 0x0f8bfbff
[    82.184] rdpSimdInit: sse2 amd64 yuv functions assigned
[    82.264] rdpScreenInit: glamor_init ok
[    82.264] rdpDri2Init:
[    82.265] (II) XRDPDEV(0): [DRI2] Setup complete
[    82.265] (II) XRDPDEV(0): [DRI2]   DRI driver: vmwgfx
[    82.265] (II) XRDPDEV(0): [DRI2]   VDPAU driver: vmwgfx
[    82.265] rdpScreenInit: rdpDri2Init ok
[    82.265] rdpScreenInit: rdpDri3Init ok
[    82.265] (==) XRDPDEV(0): Backing store enabled
[    82.265] rdpClientConInit: disconnect idle session after [0] sec
[    82.265] rdpClientConInit: kill disconnected [0] timeout [0] sec
[    82.266] rdpEglCreate: vertex_shader compiled 1
[    82.266] rdpEglCreate: fragment_shader compiled 1
[    82.267] rdpEglCreate: linked 1
[    82.267] rdpEglCreate: copy_tex_loc 0 copy_tex_size_loc 1
[    82.267] rdpEglCreate: vertex_shader compiled 1
[    82.268] rdpEglCreate: fragment_shader compiled 1
[    82.268] rdpEglCreate: linked 1
[    82.268] rdpEglCreate: yuv_tex_loc 0 yuv_tex_size_loc 1
[    82.269] rdpEglCreate: vertex_shader compiled 1
[    82.270] rdpEglCreate: fragment_shader compiled 1
[    82.276] rdpEglCreate: linked 1
[    82.276] rdpEglCreate: yuvlp_tex_loc 0 yuvlp_tex_size_loc 1
[    82.277] rdpEglCreate: vertex_shader compiled 1
[    82.280] rdpEglCreate: fragment_shader compiled 1
[    82.283] rdpEglCreate: linked 1
[    82.284] rdpEglCreate: crc_tex_loc 0 crc_tex_size_loc 1
[    82.284] rdpScreenInit: out
[    82.284] (II) Initializing extension Generic Event Extension
[    82.284] (II) Initializing extension SHAPE
[    82.284] (II) Initializing extension MIT-SHM
[    82.284] (II) Initializing extension XInputExtension
[    82.284] (II) Initializing extension XTEST
[    82.284] (II) Initializing extension BIG-REQUESTS
[    82.285] (II) Initializing extension SYNC
[    82.285] (II) Initializing extension XKEYBOARD
[    82.285] (II) Initializing extension XC-MISC
[    82.285] (II) Initializing extension SECURITY
[    82.285] (II) Initializing extension XFIXES
[    82.286] (II) Initializing extension RENDER
[    82.286] (II) Initializing extension RANDR
[    82.286] (II) Initializing extension COMPOSITE
[    82.286] (II) Initializing extension DAMAGE
[    82.286] (II) Initializing extension MIT-SCREEN-SAVER
[    82.286] (II) Initializing extension DOUBLE-BUFFER
[    82.287] (II) Initializing extension RECORD
[    82.287] (II) Initializing extension DPMS
[    82.287] (II) Initializing extension Present
[    82.287] (II) Initializing extension DRI3
[    82.287] (II) Initializing extension X-Resource
[    82.287] (II) Initializing extension XVideo
[    82.287] (II) Initializing extension XVideo-MotionCompensation
[    82.287] (II) Initializing extension SELinux
[    82.287] (II) SELinux: Disabled on system
[    82.287] (II) Initializing extension GLX
[    82.294] (II) AIGLX: Loaded and initialized vmwgfx
[    82.294] (II) GLX: Initialized DRI2 GL provider for screen 0
[    82.294] (II) Initializing extension XFree86-VidModeExtension
[    82.294] (II) Initializing extension XFree86-DGA
[    82.294] (II) Initializing extension XFree86-DRI
[    82.294] (II) Initializing extension DRI2
[    82.294] rdpCreateScreenResources:
[    82.294] rdpCreateScreenResources: create screen pixmap w 800 h 600
[    82.302] rdpCreateScreenResources: screen_tex 0x00000001
[    82.355] (II) Using input driver 'XRDPMOUSE' for 'xrdpMouse'
[    82.355] (**) Option "CorePointer"
[    82.355] (**) xrdpMouse: always reports core events
[    82.355] rdpmousePreInit: drv 0x56466f731040 info 0x5646701dad80, flags 0x0
[    82.355] (II) XINPUT: Adding extended input device "xrdpMouse" (type: Mouse, id 6)
[    82.355] rdpmouseControl: what 0
[    82.355] rdpmouseDeviceInit:
[    82.355] rdpmouseCtrl:
[    82.355] rdpRegisterInputCallback: type 1 proc 0x7f71a4467430
[    82.356] (**) xrdpMouse: (accel) keeping acceleration scheme 1
[    82.356] (**) xrdpMouse: (accel) acceleration profile 0
[    82.356] (**) xrdpMouse: (accel) acceleration factor: 2.000
[    82.356] (**) xrdpMouse: (accel) acceleration threshold: 4
[    82.356] rdpmouseControl: what 1
[    82.356] rdpmouseDeviceOn:
[    82.356] (II) Using input driver 'XRDPKEYB' for 'xrdpKeyboard'
[    82.356] (**) Option "CoreKeyboard"
[    82.356] (**) xrdpKeyboard: always reports core events
[    82.356] rdpkeybPreInit: drv 0x56466f731700 info 0x5646701dd380, flags 0x0
[    82.356] (II) XINPUT: Adding extended input device "xrdpKeyboard" (type: Keyboard, id 7)
[    82.356] rdpkeybControl: what 0
[    82.356] rdpkeybDeviceInit:
[    82.434] rdpkeybChangeKeyboardControl:
[    82.435] rdpkeybChangeKeyboardControl: autoRepeat on
[    82.435] rdpRegisterInputCallback: type 0 proc 0x7f71a35ed8e0
[    82.435] rdpkeybControl: what 1
[    82.435] rdpkeybDeviceOn:
[    82.460] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    82.460] (II) AutoAddDevices is off - not adding device.
[    82.460] (II) config/udev: Adding drm device (/dev/dri/card0)
[    82.461] (II) xfree86: Adding drm device (/dev/dri/card0)
[    82.461] (EE) systemd-logind: failed to take device /dev/dri/card0: Operation not permitted
[    82.462] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
[    82.464] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/event2)
[    82.464] (II) AutoAddDevices is off - not adding device.
[    82.465] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/mouse0)
[    82.465] (II) AutoAddDevices is off - not adding device.
[    82.466] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
[    82.466] (II) AutoAddDevices is off - not adding device.
[    82.467] (II) config/udev: Adding input device VirtualPS/2 VMware VMMouse (/dev/input/event4)
[    82.467] (II) AutoAddDevices is off - not adding device.
[    82.468] (II) config/udev: Adding input device VirtualPS/2 VMware VMMouse (/dev/input/mouse2)
[    82.468] (II) AutoAddDevices is off - not adding device.
[    82.469] (II) config/udev: Adding input device VirtualPS/2 VMware VMMouse (/dev/input/event3)
[    82.469] (II) AutoAddDevices is off - not adding device.
[    82.470] (II) config/udev: Adding input device VirtualPS/2 VMware VMMouse (/dev/input/mouse1)
[    82.470] (II) AutoAddDevices is off - not adding device.
[    82.483] rdpDeferredRandR:
[    82.484] rdpResizeSession: width 1024 height 768
[    82.484]   calling RRScreenSizeSet
[    82.484] rdpRRScreenSetSize: width 1024 height 768 mmWidth 271 mmHeight 203
[    82.484] rdpRRScreenSetSize: screen_tex 0x00000003
[    82.484] rdpRRGetInfo:
[    82.484]   screen resized to 1024x768
[    82.484]   RRScreenSizeSet ok 1
[    82.484] rdpResizeSession: width 1920 height 1080
[    82.484]   calling RRScreenSizeSet
[    82.484] rdpRRScreenSetSize: width 1920 height 1080 mmWidth 508 mmHeight 286
[    82.484] rdpRRScreenSetSize: screen_tex 0x00000004
[    82.484] rdpRRGetInfo:
[    82.484]   screen resized to 1920x1080
[    82.485]   RRScreenSizeSet ok 1
[    82.497] rdpClientConGotConnection:
[    82.497] rdpClientConGotConnection: g_sck_accept ok new_sck 7
[    82.497] rdpClientConGetConnection: idle_disconnect_timeout set to non-positive value, idle timer turned off
[    82.497] rdpAddClientConToDev: adding first clientCon 0x56467022d4c0
[    82.497] rdpClientConProcessMsgVersion: version 0 0 0 1
[    82.500] rdpClientConProcessScreenSizeMsg: set width 1920 height 1080 bpp 32
[    82.500] rdpClientConProcessScreenSizeMsg: shmemid 40 shmemptr 0x7f719a8d9000
[    82.500] rdpClientConProcessMsgClientInput: invalidate x 0 y 0 cx 1920 cy 1080
[    82.500] KbdSync: toggling num lock
[    82.500] rdpClientConProcessMsgClientInfo:
[    82.500]   got client info bytes 5752
[    82.500]   jpeg support 0
[    82.500]   offscreen support 1
[    82.500]   offscreen size 10485760
[    82.500]   offscreen entries 100
[    82.500]   client can not do offscreen to offscreen blits
[    82.500]   client can do new(color) cursor
[    82.500]   client can not do multimon
[    82.501] rdpRRSetRdpOutputs: numCrtcs 0 numOutputs 0 monitorCount 0
[    82.501] rdpRRSetRdpOutputs: add output 0 left 0 top 0 width 1920 height 1080
[    82.501] rdpLoadLayout: keylayout 0x00000410 variant  display 10
[    82.531] rdpkeybChangeKeyboardControl:
[    82.531] rdpkeybChangeKeyboardControl: autoRepeat on
[    82.532] rdpkeybChangeKeyboardControl:
[    82.532] rdpkeybChangeKeyboardControl: autoRepeat on
[    82.533] rdpkeybChangeKeyboardControl:
[    82.533] rdpkeybChangeKeyboardControl: autoRepeat on
[    82.533] rdpkeybChangeKeyboardControl:
[    82.533] rdpkeybChangeKeyboardControl: autoRepeat on
[    82.535] rdpInDeferredRepeatCallback:
[    82.535] rdpkeybChangeKeyboardControl:
[    82.535] rdpkeybChangeKeyboardControl: autoRepeat off
[    82.631] rdpInDeferredRepeatCallback:
[    82.631] rdpkeybChangeKeyboardControl:
[    82.631] rdpkeybChangeKeyboardControl: autoRepeat off
[    82.634] rdpInDeferredRepeatCallback:
[    82.634] rdpkeybChangeKeyboardControl:
[    82.634] rdpkeybChangeKeyboardControl: autoRepeat off
[    82.634] rdpInDeferredRepeatCallback:
[    82.634] rdpkeybChangeKeyboardControl:
[    82.634] rdpkeybChangeKeyboardControl: autoRepeat off
[    82.634] rdpInDeferredRepeatCallback:
[    82.634] rdpkeybChangeKeyboardControl:
[    82.634] rdpkeybChangeKeyboardControl: autoRepeat off
[    84.012] rdpmouseControl: what 2
[    84.014] rdpmouseDeviceOff:
[    84.015] rdpkeybControl: what 2
[    84.015] rdpkeybDeviceOff:
[    84.038] rdpkeybControl: what 3
[    84.038] rdpkeybUnInit: drv 0x56466f731700 info 0x5646701dd380, flags 0x0
[    84.038] rdpUnregisterInputCallback: proc 0x7f71a35ed8e0
[    84.038] rdpmouseControl: what 3
[    84.038] rdpmouseUnInit: drv 0x56466f731040 info 0x5646701dad80, flags 0x0
[    84.038] rdpUnregisterInputCallback: proc 0x7f71a4467430
[    84.039] rdpCloseScreen:
[    84.039] xorgxrdpDownDown:
[    84.039] xorgxrdpDownDown: 1
[    84.039] rdpClientConDeinit:
[    84.039] rdpClientConDeinit: disconnecting clientCon
[    84.039] rdpClientConDisconnect:
[    84.092] rdpRemoveClientConFromDev: removing clientCon 0x56467022d4c0
[    84.236] rdpClientConDeinit: deleting file /run/xrdp/sockdir/xrdp_display_10
[    84.257] rdpClientConDeinit: deleting file /run/xrdp/sockdir/xrdp_disconnect_display_10
[    84.267] (II) Server terminated successfully (0). Closing log file.
```

```
[20200501-19:24:37] [INFO ] A connection received from ::1 port 44552
[20200501-19:24:37] [INFO ] ++ created session (access granted): username pcadmin, ip ::ffff:192.168.101.101:58711 - socket: 12
[20200501-19:24:37] [INFO ] starting Xorg session...
[20200501-19:24:37] [DEBUG] Closed socket 9 (AF_INET6 :: port 5910)
[20200501-19:24:37] [DEBUG] Closed socket 9 (AF_INET6 :: port 6010)
[20200501-19:24:37] [DEBUG] Closed socket 9 (AF_INET6 :: port 6210)
[20200501-19:24:37] [DEBUG] Closed socket 8 (AF_INET6 ::1 port 3350)
[20200501-19:24:37] [INFO ] calling auth_start_session from pid 1902
[20200501-19:24:37] [DEBUG] Closed socket 7 (AF_INET6 ::1 port 3350)
[20200501-19:24:37] [DEBUG] Closed socket 8 (AF_INET6 ::1 port 3350)
[20200501-19:24:37] [INFO ] /usr/lib/xorg/Xorg :10 -auth .Xauthority -config xrdp/xorg.conf -noreset -nolisten tcp -logfile .xorgxrdp.%s.log  
[20200501-19:24:37] [CORE ] waiting for window manager (pid 1907) to exit
[20200501-19:24:40] [CORE ] window manager (pid 1907) did exit, cleaning up session
[20200501-19:24:40] [INFO ] calling auth_stop_session and auth_end from pid 1902
[20200501-19:24:40] [DEBUG] cleanup_sockets:
[20200501-19:24:40] [DEBUG] cleanup_sockets: deleting /run/xrdp/sockdir/xrdp_chansrv_audio_out_socket_10
[20200501-19:24:40] [DEBUG] cleanup_sockets: deleting /run/xrdp/sockdir/xrdp_chansrv_audio_in_socket_10
[20200501-19:24:40] [DEBUG] cleanup_sockets: deleting /run/xrdp/sockdir/xrdpapi_10
[20200501-19:24:40] [INFO ] ++ terminated session:  username pcadmin, display :10.0, session_pid 1902, ip ::ffff:192.168.101.101:58711 - socket: 12

```

---

### Post by WhiteTigerIT on 2020-05-02
I discovered that the problem is not a technical one, but a login problem.
When I connect **using RDP** from a Win10 PC to another Win10, if I use the same username as the user who is already connected at that moment, **this user is automatically disconnected**.
Instead, **using XRDP**, if I connect with the username of the user who is already connected at the time, **my connection is closed**.


In other words, either the logged in user must log out to allow me to connect to his PC, or I have to use another username.

---

