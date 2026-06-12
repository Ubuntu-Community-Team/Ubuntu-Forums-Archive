---
title: "lightdm hangs, won't start after fresh install- but worked while booting off the usb"
date: 2012-06-22
forum: Desktop Environments
---

### Post by birdzhavefangs on 2012-06-22
After struggling with getting the GUI interface running I decided to do a fresh install of Ubuntu 12.04 and by "fresh" I mean 20 minutes ago. I *know* that this hardware works with Ubuntu as I had previously had a working configuration.  However, now I can't get it to recognize the display, and it dumps you into the command line interface.

Previously (before the reinstall) I had tried all manner of NVIDIA drivers (both from repoistories and downloading directly from NVIDIA's website).

Also, the text it displays on the monitor in tty is blurry, small, and hard to read.  Grub bootloader text is fine, and it briefly displays the Ubuntu name and loading dots before dumping to the command line interface.  Reinstalling lightdm did nothing.

/var/log/Xorg.0.log
```
[   362.256] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   362.256] X Protocol Version 11, Revision 0
[   362.256] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   362.256] Current Operating System: Linux [name removed] 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
[   362.256] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=b25ab072-077d-40f1-95a4-c7fd66acd2f0 ro reboot=pci quiet splash vt.handoff=7
[   362.256] Build Date: 05 April 2012  04:32:37AM
[   362.256] xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
[   362.256] Current version of pixman: 0.24.4
[   362.256]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   362.256] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   362.256] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 22 13:55:44 2012
[   362.256] (==) Using config file: "/etc/X11/xorg.conf"
[   362.256] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   362.256] (==) No Layout section.  Using the first Screen section.
[   362.256] (==) No screen section available. Using defaults.
[   362.256] (**) |-->Screen "Default Screen Section" (0)
[   362.256] (**) |   |-->Monitor "<default monitor>"
[   362.257] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[   362.257] (**) |   |-->Device "Default Device"
[   362.257] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   362.257] (==) Automatically adding devices
[   362.257] (==) Automatically enabling devices
[   362.257] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   362.257]     Entry deleted from font path.
[   362.257] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   362.257]     Entry deleted from font path.
[   362.257] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   362.257]     Entry deleted from font path.
[   362.257] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   362.257]     Entry deleted from font path.
[   362.257] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   362.257]     Entry deleted from font path.
[   362.257] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   362.257]     Entry deleted from font path.
[   362.257] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   362.257] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   362.257] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   362.257] (II) Loader magic: 0x7f1d3c10ab00
[   362.257] (II) Module ABI versions:
[   362.257]     X.Org ANSI C Emulation: 0.4
[   362.257]     X.Org Video Driver: 11.0
[   362.257]     X.Org XInput driver : 16.0
[   362.257]     X.Org Server Extension : 6.0
[   362.258] (--) PCI:*(0:3:0:0) 10de:06f8:10de:057e rev 161, Mem @ 0xe0000000/16777216, 0xd4000000/67108864, 0xde000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/131072
[   362.258] (--) PCI: (0:4:0:0) 10de:06f8:10de:057e rev 161, Mem @ 0xdc000000/16777216, 0xd0000000/67108864, 0xda000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/131072
[   362.258] (II) Open ACPI successful (/var/run/acpid.socket)
[   362.258] (II) LoadModule: "extmod"
[   362.258] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   362.258] (II) Module extmod: vendor="X.Org Foundation"
[   362.258]     compiled for 1.11.3, module version = 1.0.0
[   362.258]     Module class: X.Org Server Extension
[   362.258]     ABI class: X.Org Server Extension, version 6.0
[   362.258] (II) Loading extension MIT-SCREEN-SAVER
[   362.258] (II) Loading extension XFree86-VidModeExtension
[   362.258] (II) Loading extension XFree86-DGA
[   362.258] (II) Loading extension DPMS
[   362.258] (II) Loading extension XVideo
[   362.259] (II) Loading extension XVideo-MotionCompensation
[   362.259] (II) Loading extension X-Resource
[   362.259] (II) LoadModule: "dbe"
[   362.259] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   362.259] (II) Module dbe: vendor="X.Org Foundation"
[   362.259]     compiled for 1.11.3, module version = 1.0.0
[   362.259]     Module class: X.Org Server Extension
[   362.259]     ABI class: X.Org Server Extension, version 6.0
[   362.259] (II) Loading extension DOUBLE-BUFFER
[   362.259] (II) LoadModule: "glx"
[   362.259] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   362.267] (II) Module glx: vendor="NVIDIA Corporation"
[   362.267]     compiled for 4.0.2, module version = 1.0.0
[   362.267]     Module class: X.Org Server Extension
[   362.267] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[   362.267] (II) Loading extension GLX
[   362.267] (II) LoadModule: "record"
[   362.267] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   362.267] (II) Module record: vendor="X.Org Foundation"
[   362.267]     compiled for 1.11.3, module version = 1.13.0
[   362.267]     Module class: X.Org Server Extension
[   362.267]     ABI class: X.Org Server Extension, version 6.0
[   362.267] (II) Loading extension RECORD
[   362.267] (II) LoadModule: "dri"
[   362.267] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   362.267] (II) Module dri: vendor="X.Org Foundation"
[   362.267]     compiled for 1.11.3, module version = 1.0.0
[   362.267]     ABI class: X.Org Server Extension, version 6.0
[   362.267] (II) Loading extension XFree86-DRI
[   362.267] (II) LoadModule: "dri2"
[   362.267] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   362.267] (II) Module dri2: vendor="X.Org Foundation"
[   362.267]     compiled for 1.11.3, module version = 1.2.0
[   362.267]     ABI class: X.Org Server Extension, version 6.0
[   362.267] (II) Loading extension DRI2
[   362.267] (==) Matched nvidia as autoconfigured driver 0
[   362.267] (==) Matched nouveau as autoconfigured driver 1
[   362.267] (==) Matched nv as autoconfigured driver 2
[   362.267] (==) Matched vesa as autoconfigured driver 3
[   362.267] (==) Matched fbdev as autoconfigured driver 4
[   362.267] (==) Assigned the driver to the xf86ConfigLayout
[   362.267] (II) LoadModule: "nvidia"
[   362.267] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   362.267] (II) Module nvidia: vendor="NVIDIA Corporation"
[   362.267]     compiled for 4.0.2, module version = 1.0.0
[   362.267]     Module class: X.Org Video Driver
[   362.268] (II) LoadModule: "nouveau"
[   362.268] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   362.268] (II) Module nouveau: vendor="X.Org Foundation"
[   362.268]     compiled for 1.11.3, module version = 0.0.16
[   362.268]     Module class: X.Org Video Driver
[   362.268]     ABI class: X.Org Video Driver, version 11.0
[   362.268] (II) LoadModule: "nv"
[   362.268] (WW) Warning, couldn't open module nv
[   362.268] (II) UnloadModule: "nv"
[   362.268] (II) Unloading nv
[   362.268] (EE) Failed to load module "nv" (module does not exist, 0)
[   362.268] (II) LoadModule: "vesa"
[   362.268] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   362.268] (II) Module vesa: vendor="X.Org Foundation"
[   362.268]     compiled for 1.11.3, module version = 2.3.0
[   362.268]     Module class: X.Org Video Driver
[   362.268]     ABI class: X.Org Video Driver, version 11.0
[   362.268] (II) LoadModule: "fbdev"
[   362.268] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   362.268] (II) Module fbdev: vendor="X.Org Foundation"
[   362.268]     compiled for 1.11.3, module version = 0.4.2
[   362.268]     ABI class: X.Org Video Driver, version 11.0
[   362.268] (==) Matched nvidia as autoconfigured driver 0
[   362.268] (==) Matched nouveau as autoconfigured driver 1
[   362.268] (==) Matched nv as autoconfigured driver 2
[   362.268] (==) Matched vesa as autoconfigured driver 3
[   362.268] (==) Matched fbdev as autoconfigured driver 4
[   362.268] (==) Assigned the driver to the xf86ConfigLayout
[   362.268] (II) LoadModule: "nvidia"
[   362.269] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   362.269] (II) Module nvidia: vendor="NVIDIA Corporation"
[   362.269]     compiled for 4.0.2, module version = 1.0.0
[   362.269]     Module class: X.Org Video Driver
[   362.269] (II) UnloadModule: "nvidia"
[   362.269] (II) Unloading nvidia
[   362.269] (II) Failed to load module "nvidia" (already loaded, 32541)
[   362.269] (II) LoadModule: "nouveau"
[   362.269] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   362.269] (II) Module nouveau: vendor="X.Org Foundation"
[   362.269]     compiled for 1.11.3, module version = 0.0.16
[   362.269]     Module class: X.Org Video Driver
[   362.269]     ABI class: X.Org Video Driver, version 11.0
[   362.269] (II) UnloadModule: "nouveau"
[   362.269] (II) Unloading nouveau
[   362.269] (II) Failed to load module "nouveau" (already loaded, 32541)
[   362.269] (II) LoadModule: "nv"
[   362.269] (WW) Warning, couldn't open module nv
[   362.269] (II) UnloadModule: "nv"
[   362.269] (II) Unloading nv
[   362.269] (EE) Failed to load module "nv" (module does not exist, 0)
[   362.269] (II) LoadModule: "vesa"
[   362.269] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   362.269] (II) Module vesa: vendor="X.Org Foundation"
[   362.269]     compiled for 1.11.3, module version = 2.3.0
[   362.269]     Module class: X.Org Video Driver
[   362.269]     ABI class: X.Org Video Driver, version 11.0
[   362.269] (II) UnloadModule: "vesa"
[   362.269] (II) Unloading vesa
[   362.269] (II) Failed to load module "vesa" (already loaded, 0)
[   362.269] (II) LoadModule: "fbdev"
[   362.269] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   362.269] (II) Module fbdev: vendor="X.Org Foundation"
[   362.269]     compiled for 1.11.3, module version = 0.4.2
[   362.269]     ABI class: X.Org Video Driver, version 11.0
[   362.269] (II) UnloadModule: "fbdev"
[   362.269] (II) Unloading fbdev
[   362.269] (II) Failed to load module "fbdev" (already loaded, 0)
[   362.269] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[   362.269] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   362.269] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[   362.269] (II) NOUVEAU driver for NVIDIA chipset families :
[   362.269]     RIVA TNT        (NV04)
[   362.269]     RIVA TNT2       (NV05)
[   362.269]     GeForce 256     (NV10)
[   362.269]     GeForce 2       (NV11, NV15)
[   362.269]     GeForce 4MX     (NV17, NV18)
[   362.269]     GeForce 3       (NV20)
[   362.269]     GeForce 4Ti     (NV25, NV28)
[   362.269]     GeForce FX      (NV3x)
[   362.269]     GeForce 6       (NV4x)
[   362.269]     GeForce 7       (G7x)
[   362.269]     GeForce 8       (G8x)
[   362.269]     GeForce GTX 200 (NVA0)
[   362.269]     GeForce GTX 400 (NVC0)
[   362.269] (II) VESA: driver for VESA chipsets: vesa
[   362.269] (II) FBDEV: driver for framebuffer: fbdev
[   362.269] (++) using VT number 7

[   362.270] (II) Loading sub module "fb"
[   362.270] (II) LoadModule: "fb"
[   362.270] (II) Loading /usr/lib/xorg/modules/libfb.so
[   362.270] (II) Module fb: vendor="X.Org Foundation"
[   362.270]     compiled for 1.11.3, module version = 1.0.0
[   362.270]     ABI class: X.Org ANSI C Emulation, version 0.4
[   362.270] (II) Loading sub module "wfb"
[   362.270] (II) LoadModule: "wfb"
[   362.270] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   362.270] (II) Module wfb: vendor="X.Org Foundation"
[   362.270]     compiled for 1.11.3, module version = 1.0.0
[   362.270]     ABI class: X.Org ANSI C Emulation, version 0.4
[   362.270] (II) Loading sub module "ramdac"
[   362.270] (II) LoadModule: "ramdac"
[   362.270] (II) Module "ramdac" already built-in
[   362.270] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   362.270] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   362.270] (II) Loading /usr/lib/xorg/modules/libfb.so
[   362.270] (WW) Falling back to old probe method for vesa
[   362.270] (WW) Falling back to old probe method for fbdev
[   362.270] (II) Loading sub module "fbdevhw"
[   362.270] (II) LoadModule: "fbdevhw"
[   362.270] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   362.270] (II) Module fbdevhw: vendor="X.Org Foundation"
[   362.270]     compiled for 1.11.3, module version = 0.0.2
[   362.270]     ABI class: X.Org Video Driver, version 11.0
[   362.270] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   362.270] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   362.270] (==) NVIDIA(0): RGB weight 888
[   362.270] (==) NVIDIA(0): Default visual is TrueColor
[   362.270] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   362.270] (**) NVIDIA(0): Option "NoLogo" "True"
[   362.270] (**) NVIDIA(0): Enabling 2D acceleration
[   362.899] (II) NVIDIA(0): NVIDIA GPU Quadro NVS 420 (G98GL) at PCI:3:0:0 (GPU-0)
[   362.899] (--) NVIDIA(0): Memory: 262144 kBytes
[   362.899] (--) NVIDIA(0): VideoBIOS: 62.98.6f.00.07
[   362.899] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   362.899] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   362.937] (--) NVIDIA(0): Connected display device(s) on Quadro NVS 420 at PCI:3:0:0
[   362.937] (--) NVIDIA(0):     none
[   362.937] (EE) NVIDIA(0): No display devices found for this X screen.
[   363.179] (II) UnloadModule: "nvidia"
[   363.179] (II) Unloading nvidia
[   363.179] (II) UnloadModule: "wfb"
[   363.179] (II) Unloading wfb
[   363.179] (II) UnloadModule: "fb"
[   363.179] (II) Unloading fb
[   363.179] (EE) Screen(s) found, but none have a usable configuration.
[   363.179] 
Fatal server error:
[   363.179] no screens found
[   363.179] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   363.179] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   363.179] 
[   363.183]  ddxSigGiveUp: Closing log
[   363.183] Server terminated with error (1). Closing log file.

```/var/log/lightdm/lightdm.log
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=2233
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: Using VT 7
[+0.00s] DEBUG: Activating VT 7
[+0.01s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: Launching X Server
[+0.01s] DEBUG: Launching process 2239: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.94s] DEBUG: Process 2239 exited with return value 1
[+0.94s] DEBUG: X server stopped
[+0.94s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.94s] DEBUG: Releasing VT 7
[+0.94s] DEBUG: Display server stopped
[+0.94s] DEBUG: Stopping display
[+0.94s] DEBUG: Display stopped
[+0.94s] DEBUG: Stopping X local seat, failed to start a display
[+0.94s] DEBUG: Stopping seat
[+0.94s] DEBUG: Seat stopped
[+0.94s] DEBUG: Required seat has stopped
[+0.94s] DEBUG: Stopping display manager
[+0.94s] DEBUG: Display manager stopped
[+0.94s] DEBUG: Stopping daemon
[+0.94s] DEBUG: Exiting with return value 1
```/var/log/lightdm/x-0.log
```

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux [name removed] 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=b25ab072-077d-40f1-95a4-c7fd66acd2f0 ro reboot=pci quiet splash vt.handoff=7
Build Date: 05 April 2012  04:32:37AM
xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 22 13:55:44 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) NVIDIA(0): No display devices found for this X screen.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.

```lspci | grep VGA
03:00.0 VGA compatible controller: NVIDIA Corporation G98 [Quadro NVS 420] (rev a1)

---

