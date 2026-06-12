---
title: "No screen found"
date: 2013-07-10
forum: Desktop Environments
---

### Post by gogonummu on 2013-07-10
Hi,

After a ubuntu crash, i cannot anymore load my unity desktop, even with the failsafe mode. However, I can load nautilus by opening a console and typing nautilus...
[Edit : when I reboot, the computer cannot load the screen and goes directly to tty1. In order to have the graphic mode, i have to first open the recovery mode, then type resume (but this does not open unity as well). And I have no sound...]

I randomely tried somethings, but i cannot see where the problem comes from : I tried to uninstall nvidia, and to reinstall it (it used to work with nvidia better than without)

```
sudo service lightdm restart
```
```
unity --reset
```
```
sudo rm /etc/X11/xorg.conf
```
```
sudo startx
```

Here are other commands i tried to see where the problem could come from :

```
dgaudin@prometeodg:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1c.6 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 7 (rev c4)
00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106GL [Quadro 2000] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF106 High Definition Audio Controller (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
06:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
```

```
more nvidia-bug-report.log.gz
[ATTACH]244583[/ATTACH]
```


```
dgaudin@prometeodg:/var/log$ more Xorg.0.log
[    11.141] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    11.141] X Protocol Version 11, Revision 0
[    11.141] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    11.141] Current Operating System: Linux prometeodg 3.2.0-49-generic #75-Ubuntu SMP Tue Jun 18
 17:39:32 UTC 2013 x86_64
[    11.141] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-49-generic root=UUID=e62586e5-a49
1-4199-a8b5-66a56348038c ro recovery nomodeset
[    11.141] Build Date: 11 April 2013  01:05:39PM
[    11.141] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu
.com/support) 
[    11.141] Current version of pixman: 0.24.4
[    11.141]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    11.141] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.141] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 10 11:00:49 2013
[    11.150] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.151] (==) No Layout section.  Using the first Screen section.
[    11.151] (==) No screen section available. Using defaults.
[    11.151] (**) |-->Screen "Default Screen Section" (0)
[    11.151] (**) |   |-->Monitor "<default monitor>"
[    11.151] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    11.151] (==) Automatically adding devices
[    11.151] (==) Automatically enabling devices
[    11.151] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.151]     Entry deleted from font path.
[    11.151] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    11.151] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/ex
tra-modules,/usr/lib/xorg/modules"
[    11.151] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.151] (II) Loader magic: 0x7f6e74ea3b00
[    11.151] (II) Module ABI versions:
[    11.151]     X.Org ANSI C Emulation: 0.4
[    11.151]     X.Org Video Driver: 11.0
[    11.151]     X.Org XInput driver : 16.0
[    11.151]     X.Org Server Extension : 6.0
[    11.151] (--) PCI:*(0:1:0:0) 10de:0dd8:10de:084a rev 161, Mem @ 0xf4000000/33554432, 0xe800000
0/134217728, 0xf0000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    11.151] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.151] (II) LoadModule: "extmod"
[    11.153] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.153] (II) Module extmod: vendor="X.Org Foundation"
[    11.153]     compiled for 1.11.3, module version = 1.0.0
[    11.153]     Module class: X.Org Server Extension
[    11.153]     ABI class: X.Org Server Extension, version 6.0
[    11.153] (II) Loading extension MIT-SCREEN-SAVER
[    11.153] (II) Loading extension XFree86-VidModeExtension
[    11.153] (II) Loading extension XFree86-DGA
[    11.153] (II) Loading extension DPMS
[    11.153] (II) Loading extension XVideo
[    11.153] (II) Loading extension XVideo-MotionCompensation
[    11.153] (II) Loading extension X-Resource
[    11.153] (II) LoadModule: "dbe"
[    11.153] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.153] (II) Module dbe: vendor="X.Org Foundation"
[    11.153]     compiled for 1.11.3, module version = 1.0.0
[    11.153]     Module class: X.Org Server Extension
[    11.153]     ABI class: X.Org Server Extension, version 6.0
[    11.153] (II) Loading extension DOUBLE-BUFFER
[    11.153] (II) LoadModule: "glx"
[    11.153] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    11.158] (II) Module glx: vendor="NVIDIA Corporation"
[    11.158]     compiled for 4.0.2, module version = 1.0.0
[    11.158]     Module class: X.Org Server Extension
[    11.158] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[    11.158] (II) Loading extension GLX
[    11.158] (II) LoadModule: "record"
[    11.158] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.158] (II) Module record: vendor="X.Org Foundation"
[    11.158]     compiled for 1.11.3, module version = 1.13.0
[    11.158]     Module class: X.Org Server Extension
[    11.158]     ABI class: X.Org Server Extension, version 6.0
[    11.158] (II) Loading extension RECORD
[    11.158] (II) LoadModule: "dri"
[    11.158] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.158] (II) Module dri: vendor="X.Org Foundation"
[    11.158]     compiled for 1.11.3, module version = 1.0.0
[    11.158]     ABI class: X.Org Server Extension, version 6.0
[    11.158] (II) Loading extension XFree86-DRI
[    11.158] (II) LoadModule: "dri2"
[    11.159] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.159] (II) Module dri2: vendor="X.Org Foundation"
[    11.159]     compiled for 1.11.3, module version = 1.2.0
[    11.159]     ABI class: X.Org Server Extension, version 6.0
[    11.159] (II) Loading extension DRI2
[    11.159] (==) Matched nvidia as autoconfigured driver 0
[    11.159] (==) Matched nouveau as autoconfigured driver 1
[    11.159] (==) Matched nv as autoconfigured driver 2
[    11.159] (==) Matched vesa as autoconfigured driver 3
[    11.159] (==) Matched fbdev as autoconfigured driver 4
[    11.159] (==) Assigned the driver to the xf86ConfigLayout
[    11.159] (II) LoadModule: "nvidia"
[    11.159] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    11.159] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.159]     compiled for 4.0.2, module version = 1.0.0
[    11.159]     Module class: X.Org Video Driver
[    11.159] (II) LoadModule: "nouveau"
[    11.159] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    11.160] (II) Module nouveau: vendor="X.Org Foundation"
[    11.160]     compiled for 1.11.3, module version = 1.0.2
[    11.160]     Module class: X.Org Video Driver
[    11.160]     ABI class: X.Org Video Driver, version 11.0
[    11.160] (II) LoadModule: "nv"
[    11.160] (WW) Warning, couldn't open module nv

[    11.160] (II) UnloadModule: "nv"
[    11.160] (II) Unloading nv
[    11.160] (EE) Failed to load module "nv" (module does not exist, 0)
[    11.160] (II) LoadModule: "vesa"
[    11.160] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.160] (II) Module vesa: vendor="X.Org Foundation"
[    11.160]     compiled for 1.11.3, module version = 2.3.0
[    11.160]     Module class: X.Org Video Driver
[    11.160]     ABI class: X.Org Video Driver, version 11.0
[    11.160] (II) LoadModule: "fbdev"
[    11.160] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.160] (II) Module fbdev: vendor="X.Org Foundation"
[    11.160]     compiled for 1.11.3, module version = 0.4.2
[    11.160]     ABI class: X.Org Video Driver, version 11.0
[    11.160] (==) Matched nvidia as autoconfigured driver 0
[    11.160] (==) Matched nouveau as autoconfigured driver 1
[    11.160] (==) Matched nv as autoconfigured driver 2
[    11.160] (==) Matched vesa as autoconfigured driver 3
[    11.160] (==) Matched fbdev as autoconfigured driver 4
[    11.160] (==) Assigned the driver to the xf86ConfigLayout
[    11.160] (II) LoadModule: "nvidia"
[    11.160] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    11.160] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.160]     compiled for 4.0.2, module version = 1.0.0
[    11.160]     Module class: X.Org Video Driver
[    11.160] (II) UnloadModule: "nvidia"
[    11.160] (II) Unloading nvidia
[    11.160] (II) Failed to load module "nvidia" (already loaded, 32622)
[    11.160] (II) LoadModule: "nouveau"
[    11.160] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    11.160] (II) Module nouveau: vendor="X.Org Foundation"
[    11.160]     compiled for 1.11.3, module version = 1.0.2
[    11.160]     Module class: X.Org Video Driver
[    11.160]     ABI class: X.Org Video Driver, version 11.0
[    11.160] (II) UnloadModule: "nouveau"
[    11.160] (II) Unloading nouveau
[    11.160] (II) Failed to load module "nouveau" (already loaded, 32622)
[    11.160] (II) LoadModule: "nv"
[    11.160] (WW) Warning, couldn't open module nv
[    11.160] (II) UnloadModule: "nv"
[    11.161] (II) Unloading nv
[    11.161] (EE) Failed to load module "nv" (module does not exist, 0)
[    11.161] (II) LoadModule: "vesa"
[    11.161] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.161] (II) Module vesa: vendor="X.Org Foundation"
[    11.161]     compiled for 1.11.3, module version = 2.3.0
[    11.161]     Module class: X.Org Video Driver
[    11.161]     ABI class: X.Org Video Driver, version 11.0
[    11.161] (II) UnloadModule: "vesa"
[    11.161] (II) Unloading vesa
[    11.161] (II) Failed to load module "vesa" (already loaded, 0)
[    11.161] (II) LoadModule: "fbdev"
[    11.161] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.161] (II) Module fbdev: vendor="X.Org Foundation"
[    11.161]     compiled for 1.11.3, module version = 0.4.2
[    11.161]     ABI class: X.Org Video Driver, version 11.0
[    11.161] (II) UnloadModule: "fbdev"
[    11.161] (II) Unloading fbdev
[    11.161] (II) Failed to load module "fbdev" (already loaded, 0)
[    11.161] (II) NVIDIA dlloader X Driver  304.88  Wed Mar 27 14:28:14 PDT 2013
[    11.161] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.161] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    11.161] (II) NOUVEAU driver for NVIDIA chipset families :
[    11.161]     RIVA TNT        (NV04)
[    11.161]     RIVA TNT2       (NV05)
[    11.161]     GeForce 256     (NV10)
[    11.161]     GeForce 2       (NV11, NV15)
[    11.161]     GeForce 4MX     (NV17, NV18)
[    11.161]     GeForce 3       (NV20)
[    11.161]     GeForce 4Ti     (NV25, NV28)
[    11.161]     GeForce FX      (NV3x)
[    11.161]     GeForce 6       (NV4x)
[    11.161]     GeForce 7       (G7x)
[    11.161]     GeForce 8       (G8x)
[    11.161]     GeForce GTX 200 (NVA0)
[    11.161]     GeForce GTX 400 (NVC0)
[    11.161] (II) VESA: driver for VESA chipsets: vesa
[    11.161] (II) FBDEV: driver for framebuffer: fbdev
[    11.161] (++) using VT number 7

[    11.165] (II) Loading sub module "fb"
[    11.165] (II) LoadModule: "fb"
[    11.165] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.165] (II) Module fb: vendor="X.Org Foundation"
[    11.165]     compiled for 1.11.3, module version = 1.0.0
[    11.165]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.165] (II) Loading sub module "wfb"
[    11.165] (II) LoadModule: "wfb"
[    11.165] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.165] (II) Module wfb: vendor="X.Org Foundation"
[    11.165]     compiled for 1.11.3, module version = 1.0.0
[    11.165]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.165] (II) Loading sub module "ramdac"
[    11.165] (II) LoadModule: "ramdac"
[    11.165] (II) Module "ramdac" already built-in
[    11.165] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    11.165] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.165] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.165] (WW) Falling back to old probe method for vesa
[    11.165] (WW) Falling back to old probe method for fbdev
[    11.165] (II) Loading sub module "fbdevhw"
[    11.165] (II) LoadModule: "fbdevhw"
[    11.165] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.165] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.165]     compiled for 1.11.3, module version = 0.0.2
[    11.165]     ABI class: X.Org Video Driver, version 11.0
[    11.165] (EE) open /dev/fb0: No such file or directory
[    11.166] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    11.166] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    11.166] (==) NVIDIA(0): RGB weight 888
[    11.166] (==) NVIDIA(0): Default visual is TrueColor
[    11.166] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.166] (**) NVIDIA(0): Enabling 2D acceleration
[    11.724] (II) NVIDIA(GPU-0): Display (Samsung S24B350 (DFP-0)) does not support NVIDIA 3D
[    11.724] (II) NVIDIA(GPU-0):     Vision stereo.
[    11.725] (II) NVIDIA(0): NVIDIA GPU Quadro 2000 (GF106GL) at PCI:1:0:0 (GPU-0)
[    11.725] (--) NVIDIA(0): Memory: 1048576 kBytes
[    11.725] (--) NVIDIA(0): VideoBIOS: 70.06.3f.00.01
[    11.725] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    11.725] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    11.729] (--) NVIDIA(0): Valid display device(s) on Quadro 2000 at PCI:1:0:0
[    11.729] (--) NVIDIA(0):     CRT-0
[    11.729] (--) NVIDIA(0):     Samsung S24B350 (DFP-0) (connected)
[    11.729] (--) NVIDIA(0):     DFP-1
[    11.729] (--) NVIDIA(0):     DFP-2
[    11.729] (--) NVIDIA(0):     DFP-3
[    11.729] (--) NVIDIA(0):     DFP-4
[    11.729] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    11.729] (--) NVIDIA(0): Samsung S24B350 (DFP-0): 330.0 MHz maximum pixel clock
[    11.729] (--) NVIDIA(0): Samsung S24B350 (DFP-0): Internal Dual Link TMDS
[    11.729] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    11.729] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    11.729] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[    11.729] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[    11.729] (--) NVIDIA(0): DFP-3: 480.0 MHz maximum pixel clock
[    11.729] (--) NVIDIA(0): DFP-3: Internal DisplayPort
[    11.729] (--) NVIDIA(0): DFP-4: 480.0 MHz maximum pixel clock
[    11.729] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    11.729] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    11.729] (**) NVIDIA(0):     device Samsung S24B350 (DFP-0) (Using EDID frequencies has
[    11.729] (**) NVIDIA(0):     been enabled on all display devices.)
[    11.729] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    11.729] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    11.729] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    11.729] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    11.730] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    11.730] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    11.730] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    11.730] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    11.730] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    11.730] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    11.730] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    11.730] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    11.730] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    11.730] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    11.730] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    11.731] (==) NVIDIA(0): 
[    11.731] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    11.731] (==) NVIDIA(0):     will be used as the requested mode.
[    11.731] (==) NVIDIA(0): 
[    11.731] (II) NVIDIA(0): Validated MetaModes:
[    11.731] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[    11.731] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    11.766] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[    11.766] (--) NVIDIA(0):     option
[    11.766] (WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
[    11.766] (WW) NVIDIA(0):     UBB.
[    11.766] (II) UnloadModule: "nouveau"
[    11.766] (II) Unloading nouveau
[    11.766] (II) UnloadModule: "vesa"
[    11.766] (II) Unloading vesa
[    11.766] (II) UnloadModule: "fbdev"
[    11.766] (II) Unloading fbdev
[    11.766] (II) UnloadModule: "fbdevhw"
[    11.766] (II) Unloading fbdevhw
[    11.766] (--) Depth 24 pixmap format is 32 bpp
[    11.766] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    11.766] (II) NVIDIA:     access.
[    11.772] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[    11.807] (II) Loading extension NV-GLX
[    11.852] (==) NVIDIA(0): Disabling shared memory pixmaps
[    11.852] (==) NVIDIA(0): Backing store disabled
[    11.852] (==) NVIDIA(0): Silken mouse enabled
[    11.852] (==) NVIDIA(0): DPMS enabled
[    11.852] (II) Loading extension NV-CONTROL
[    11.852] (II) Loading extension XINERAMA
[    11.852] (II) Loading sub module "dri2"
[    11.852] (II) LoadModule: "dri2"
[    11.852] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.852] (II) Module dri2: vendor="X.Org Foundation"
[    11.852]     compiled for 1.11.3, module version = 1.2.0
[    11.852]     ABI class: X.Org Server Extension, version 6.0
[    11.852] (II) NVIDIA(0): [DRI2] Setup complete
[    11.852] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    11.852] (--) RandR disabled
[    11.852] (II) Initializing built-in extension Generic Event Extension
[    11.852] (II) Initializing built-in extension SHAPE
[    11.852] (II) Initializing built-in extension MIT-SHM
[    11.852] (II) Initializing built-in extension XInputExtension
[    11.852] (II) Initializing built-in extension XTEST
[    11.852] (II) Initializing built-in extension BIG-REQUESTS
[    11.852] (II) Initializing built-in extension SYNC
[    11.852] (II) Initializing built-in extension XKEYBOARD
[    11.852] (II) Initializing built-in extension XC-MISC
[    11.852] (II) Initializing built-in extension SECURITY
[    11.852] (II) Initializing built-in extension XINERAMA
[    11.852] (II) Initializing built-in extension XFIXES
[    11.852] (II) Initializing built-in extension RENDER
[    11.852] (II) Initializing built-in extension RANDR
[    11.852] (II) Initializing built-in extension COMPOSITE
[    11.852] (II) Initializing built-in extension DAMAGE
[    11.853] (II) Initializing extension GLX
[    11.866] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.
xkm
[    11.867] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    11.867] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.867] (II) LoadModule: "evdev"
[    11.867] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.867] (II) Module evdev: vendor="X.Org Foundation"
[    11.867]     compiled for 1.11.3, module version = 2.7.0
[    11.867]     Module class: X.Org XInput Driver
[    11.867]     ABI class: X.Org XInput driver, version 16.0
[    11.867] (II) Using input driver 'evdev' for 'Power Button'
[    11.867] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.867] (**) Power Button: always reports core events
[    11.867] (**) evdev: Power Button: Device: "/dev/input/event1"
[    11.868] (--) evdev: Power Button: Vendor 0 Product 0x1
[    11.868] (--) evdev: Power Button: Found keys
[    11.868] (II) evdev: Power Button: Configuring as keyboard
[    11.868] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/eve
nt1"
[    11.868] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    11.868] (**) Option "xkb_rules" "evdev"
[    11.868] (**) Option "xkb_model" "pc105"
[    11.868] (**) Option "xkb_layout" "it"
[    11.868] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.
xkm
[    11.869] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    11.869] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.869] (II) Using input driver 'evdev' for 'Power Button'
[    11.869] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.869] (**) Power Button: always reports core events
[    11.869] (**) evdev: Power Button: Device: "/dev/input/event0"
[    11.869] (--) evdev: Power Button: Vendor 0 Product 0x1
[    11.869] (--) evdev: Power Button: Found keys
[    11.869] (II) evdev: Power Button: Configuring as keyboard
[    11.869] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input
/input0/event0"
[    11.869] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    11.869] (**) Option "xkb_rules" "evdev"
[    11.869] (**) Option "xkb_model" "pc105"
[    11.869] (**) Option "xkb_layout" "it"
[    11.869] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event16)
[    11.869] (II) No input driver specified, ignoring this device.
[    11.869] (II) This device may have been added with another device file.
[    11.869] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event17)
[    11.869] (II) No input driver specified, ignoring this device.
[    11.869] (II) This device may have been added with another device file.
[    11.869] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event18)
[    11.869] (II) No input driver specified, ignoring this device.
[    11.869] (II) This device may have been added with another device file.
[    11.869] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event19)
[    11.869] (II) No input driver specified, ignoring this device.
[    11.869] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event10)
[    11.870] (II) No input driver specified, ignoring this device.
[    11.870] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event
11)
[    11.870] (II) No input driver specified, ignoring this device.
[    11.870] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device HDA Intel PCH Line-Out Side (/dev/input/event12
)
[    11.870] (II) No input driver specified, ignoring this device.
[    11.870] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device HDA Intel PCH Line-Out CLFE (/dev/input/event13
)
[    11.870] (II) No input driver specified, ignoring this device.
[    11.870] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device HDA Intel PCH Line-Out Surround (/dev/input/eve
nt14)
[    11.870] (II) No input driver specified, ignoring this device.
[    11.870] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device HDA Intel PCH Line-Out Front (/dev/input/event1
5)
[    11.870] (II) No input driver specified, ignoring this device.
[    11.870] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[    11.870] (II) No input driver specified, ignoring this device.
[    11.870] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event9)
[    11.870] (II) No input driver specified, ignoring this device.
[    11.870] (II) This device may have been added with another device file.
[    11.870] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event2)
[    11.870] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.870] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    11.870] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.871] (**) Logitech USB Keyboard: always reports core events
[    11.871] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event2"
[    11.871] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    11.871] (--) evdev: Logitech USB Keyboard: Found keys
[    11.871] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    11.871] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb
5/5-1/5-1:1.0/input/input2/event2"
[    11.871] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id
 8)
[    11.871] (**) Option "xkb_rules" "evdev"
[    11.871] (**) Option "xkb_model" "pc105"
[    11.871] (**) Option "xkb_layout" "it"
[    11.871] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event3)
[    11.871] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.871] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    11.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.871] (**) Logitech USB Keyboard: always reports core events
[    11.871] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event3"
[    11.871] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    11.871] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    11.871] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    11.871] (--) evdev: Logitech USB Keyboard: Found keys
[    11.871] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    11.871] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    11.871] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb
5/5-1/5-1:1.1/input/input3/event3"
[    11.871] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id
 9)
[    11.871] (**) Option "xkb_rules" "evdev"
[    11.871] (**) Option "xkb_model" "pc105"
[    11.871] (**) Option "xkb_layout" "it"
[    11.871] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    11.871] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    11.871] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    11.871] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    11.871] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    11.871] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event4)
[    11.871] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.871] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    11.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.871] (**) Logitech USB Keyboard: always reports core events
[    11.871] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event4"
[    11.871] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    11.871] (--) evdev: Logitech USB Keyboard: Found keys
[    11.871] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    11.871] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2
-1.6:1.0/input/input4/event4"
[    11.871] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id
 10)
[    11.871] (**) Option "xkb_rules" "evdev"
[    11.871] (**) Option "xkb_model" "pc105"
[    11.871] (**) Option "xkb_layout" "it"
[    11.872] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event5)
[    11.872] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.872] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    11.872] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.872] (**) Logitech USB Keyboard: always reports core events
[    11.872] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event5"
[    11.872] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    11.872] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    11.872] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    11.872] (--) evdev: Logitech USB Keyboard: Found keys
[    11.872] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    11.872] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    11.872] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2
-1.6:1.1/input/input5/event5"
[    11.872] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id
 11)
[    11.872] (**) Option "xkb_rules" "evdev"
[    11.872] (**) Option "xkb_model" "pc105"
[    11.872] (**) Option "xkb_layout" "it"
[    11.872] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    11.872] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    11.872] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    11.872] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    11.872] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    11.872] (II) config/udev: Adding input device Avago USB LaserStream(TM) Mouse (/dev/input/eve
nt6)
[    11.872] (**) Avago USB LaserStream(TM) Mouse: Applying InputClass "evdev pointer catchall"
[    11.872] (II) Using input driver 'evdev' for 'Avago USB LaserStream(TM) Mouse'
[    11.872] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.872] (**) Avago USB LaserStream(TM) Mouse: always reports core events
[    11.872] (**) evdev: Avago USB LaserStream(TM) Mouse: Device: "/dev/input/event6"
[    11.872] (--) evdev: Avago USB LaserStream(TM) Mouse: Vendor 0x192f Product 0x716
[    11.872] (--) evdev: Avago USB LaserStream(TM) Mouse: Found 3 mouse buttons
[    11.872] (--) evdev: Avago USB LaserStream(TM) Mouse: Found scroll wheel(s)
[    11.872] (--) evdev: Avago USB LaserStream(TM) Mouse: Found relative axes
[    11.872] (--) evdev: Avago USB LaserStream(TM) Mouse: Found x and y relative axes
[    11.872] (II) evdev: Avago USB LaserStream(TM) Mouse: Configuring as mouse
[    11.872] (II) evdev: Avago USB LaserStream(TM) Mouse: Adding scrollwheel support
[    11.872] (**) evdev: Avago USB LaserStream(TM) Mouse: YAxisMapping: buttons 4 and 5
[    11.872] (**) evdev: Avago USB LaserStream(TM) Mouse: EmulateWheelButton: 4, EmulateWheelInert
ia: 10, EmulateWheelTimeout: 200
[    11.872] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2
-1.8:1.0/input/input6/event6"
[    11.872] (II) XINPUT: Adding extended input device "Avago USB LaserStream(TM) Mouse" (type: MO
USE, id 12)
[    11.872] (II) evdev: Avago USB LaserStream(TM) Mouse: initialized for relative axes.
[    11.872] (**) Avago USB LaserStream(TM) Mouse: (accel) keeping acceleration scheme 1
[    11.872] (**) Avago USB LaserStream(TM) Mouse: (accel) acceleration profile 0
[    11.872] (**) Avago USB LaserStream(TM) Mouse: (accel) acceleration factor: 2.000
[    11.872] (**) Avago USB LaserStream(TM) Mouse: (accel) acceleration threshold: 4
[    11.872] (II) config/udev: Adding input device Avago USB LaserStream(TM) Mouse (/dev/input/mou
se0)
[    11.872] (II) No input driver specified, ignoring this device.
[    11.872] (II) This device may have been added with another device file.
[    11.873] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event7)
[    11.873] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    11.873] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    11.873] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.873] (**) Eee PC WMI hotkeys: always reports core events
[    11.873] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event7"
[    11.873] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    11.873] (--) evdev: Eee PC WMI hotkeys: Found keys
[    11.873] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    11.873] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input7/event7"
[    11.873] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 13
)
[    11.873] (**) Option "xkb_rules" "evdev"
[    11.873] (**) Option "xkb_model" "pc105"
[    11.873] (**) Option "xkb_layout" "it"
[    11.911] (II) NVIDIA(GPU-0): Display (Samsung S24B350 (DFP-0)) does not support NVIDIA 3D
[    11.911] (II) NVIDIA(GPU-0):     Vision stereo.
[    11.911] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    11.911] (**) NVIDIA(0):     device Samsung S24B350 (DFP-0) (Using EDID frequencies has
[    11.911] (**) NVIDIA(0):     been enabled on all display devices.)
[    11.911] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    11.911] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    11.911] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    11.911] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    11.911] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    11.911] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    11.911] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    11.911] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    11.911] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    11.911] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    11.911] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    11.911] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    11.911] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    11.911] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    11.911] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    12.036] (II) NVIDIA(GPU-0): Display (Samsung S24B350 (DFP-0)) does not support NVIDIA 3D
[    12.036] (II) NVIDIA(GPU-0):     Vision stereo.
[    12.036] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    12.036] (**) NVIDIA(0):     device Samsung S24B350 (DFP-0) (Using EDID frequencies has
[    12.036] (**) NVIDIA(0):     been enabled on all display devices.)
[    12.036] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    12.036] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    12.036] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    12.036] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    12.036] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    12.036] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    12.036] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    12.036] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    12.036] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    12.036] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    12.036] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    12.036] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    12.036] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    12.036] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    12.036] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    13.156] (II) NVIDIA(GPU-0): Display (Samsung S24B350 (DFP-0)) does not support NVIDIA 3D
[    13.156] (II) NVIDIA(GPU-0):     Vision stereo.
[    13.156] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    13.156] (**) NVIDIA(0):     device Samsung S24B350 (DFP-0) (Using EDID frequencies has
[    13.156] (**) NVIDIA(0):     been enabled on all display devices.)
[    13.156] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    13.156] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    13.156] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    13.156] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    13.156] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[    13.156] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    13.156] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[    13.156] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    13.156] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    13.156] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[    13.156] (WW) NVIDIA(GPU-0): The EDID for Samsung S24B350 (DFP-0) contradicts itself: mode
[    13.156] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[    13.156] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    13.156] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    13.156] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[    18.269] (II) XKB: reuse xkmfile /var/lib/xkb/server-578FE579C1DA334EA8BF25F338A218BFA489E7F5.
xkm

```

```
dgaudin@prometeodg:~$ more  /var/log/Xorg.failsafe.log
[    10.751] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    10.751] X Protocol Version 11, Revision 0
[    10.752] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    10.752] Current Operating System: Linux prometeodg 3.2.0-49-generic #75-Ubu
ntu SMP Tue Jun 18 17:39:32 UTC 2013 x86_64
[    10.752] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-49-generic root
=UUID=e62586e5-a491-4199-a8b5-66a56348038c ro recovery nomodeset
[    10.752] Build Date: 11 April 2013  01:05:39PM
[    10.752] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see
 http://www.ubuntu.com/support) 
[    10.752] Current version of pixman: 0.24.4
[    10.752]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    10.752] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.753] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Jul 10 11:51
:07 2013
[    10.754] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[    10.754] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.756] (==) No Layout section.  Using the first Screen section.
[    10.756] (**) |-->Screen "Default Screen" (0)
[    10.756] (**) |   |-->Monitor "Configured Monitor"
[    10.756] (**) |   |-->Device "Configured Video Device"
[    10.756] (==) Automatically adding devices
[    10.756] (==) Automatically enabling devices
[    10.758] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.758]     Entry deleted from font path.
[    10.760] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    10.760] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-module
s,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.760] (II) The server relies on udev to provide the list of input devices
.
    If no devices become available, reconfigure udev or disable AutoAddDevic
es.
[    10.761] (II) Loader magic: 0x7f8f7ba27b00
[    10.761] (II) Module ABI versions:
[    10.761]     X.Org ANSI C Emulation: 0.4
[    10.761]     X.Org Video Driver: 11.0
[    10.761]     X.Org XInput driver : 16.0
[    10.761]     X.Org Server Extension : 6.0
[    10.761] (--) PCI:*(0:1:0:0) 10de:0dd8:10de:084a rev 161, Mem @ 0xf4000000/3
3554432, 0xe8000000/134217728, 0xf0000000/67108864, I/O @ 0x0000e000/128, BIOS @
 0x????????/524288
[    10.761] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or dire
ctory)
[    10.761] (II) LoadModule: "extmod"
[    10.766] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    10.768] (II) Module extmod: vendor="X.Org Foundation"
[    10.768]     compiled for 1.11.3, module version = 1.0.0
[    10.768]     Module class: X.Org Server Extension
[    10.768]     ABI class: X.Org Server Extension, version 6.0
[    10.768] (II) Loading extension MIT-SCREEN-SAVER
[    10.768] (II) Loading extension XFree86-VidModeExtension
[    10.768] (II) Loading extension XFree86-DGA
[    10.768] (II) Loading extension DPMS
[    10.768] (II) Loading extension XVideo
[    10.768] (II) Loading extension XVideo-MotionCompensation
[    10.768] (II) Loading extension X-Resource
[    10.768] (II) LoadModule: "dbe"
[    10.768] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    10.769] (II) Module dbe: vendor="X.Org Foundation"
[    10.769]     compiled for 1.11.3, module version = 1.0.0
[    10.769]     Module class: X.Org Server Extension
[    10.769]     ABI class: X.Org Server Extension, version 6.0
[    10.769] (II) Loading extension DOUBLE-BUFFER
[    10.769] (II) LoadModule: "glx"
[    10.769] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    10.916] (II) Module glx: vendor="NVIDIA Corporation"
[    10.916]     compiled for 4.0.2, module version = 1.0.0
[    10.916]     Module class: X.Org Server Extension
[    10.916] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[    10.916] (II) Loading extension GLX
[    10.916] (II) LoadModule: "record"
[    10.916] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    10.917] (II) Module record: vendor="X.Org Foundation"
[    10.917]     compiled for 1.11.3, module version = 1.13.0
[    10.917]     Module class: X.Org Server Extension
[    10.917]     ABI class: X.Org Server Extension, version 6.0
[    10.917] (II) Loading extension RECORD
[    10.917] (II) LoadModule: "dri"
[    10.917] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    10.918] (II) Module dri: vendor="X.Org Foundation"
[    10.918]     compiled for 1.11.3, module version = 1.0.0
[    10.918]     ABI class: X.Org Server Extension, version 6.0
[    10.918] (II) Loading extension XFree86-DRI
[    10.918] (II) LoadModule: "dri2"
[    10.918] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    10.919] (II) Module dri2: vendor="X.Org Foundation"
[    10.919]     compiled for 1.11.3, module version = 1.2.0
[    10.919]     ABI class: X.Org Server Extension, version 6.0
[    10.919] (II) Loading extension DRI2
[    10.919] (II) LoadModule: "vesa"
[    10.919] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.919] (II) Module vesa: vendor="X.Org Foundation"
[    10.919]     compiled for 1.11.3, module version = 2.3.0
[    10.919]     Module class: X.Org Video Driver
[    10.919]     ABI class: X.Org Video Driver, version 11.0
[    10.920] (II) VESA: driver for VESA chipsets: vesa
[    10.920] (--) using VT number 2

[    10.928] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.928] vesa: Ignoring device with a bound kernel driver
[    10.928] (WW) Falling back to old probe method for vesa
[    10.928] (II) UnloadModule: "vesa"
[    10.928] (II) Unloading vesa
[    10.928] (EE) Screen(s) found, but none have a usable configuration.
[    10.928] 
Fatal server error:
[    10.928] no screens found
[    10.928] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    10.928] Please also check the log file at "/var/log/Xorg.failsafe.log" for 
additional information.
[    10.928] 
[    10.934]  ddxSigGiveUp: Closing log
[    10.934] Server terminated with error (1). Closing log file.
```


Thanks for your help !

---

### Post by dino99 on 2013-07-10
open a terminal to run each command below, one by one:

dconf reset -f /org/compiz/
setsid unity

---

### Post by gogonummu on 2013-07-10
Hi dino99,

Thanks for your answer.  

sudo dconf reset -f  /org/compiz/ does not output anything
setsid unity does not solve the problem (the screen is reseted and I go back to the login screen, but when I log in again, unity is still not loaded) :(

---

### Post by gogonummu on 2013-07-10
I just tried :

```
dgaudin@prometeodg:~$ unity-2d-panel &
[2] 4583
dgaudin@prometeodg:~$ unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
unity-2d-panel: [WARNING] void GnomeSessionClient::slotRegisterClientFinished(QDBusPendingCallWatcher*): Failed to register with GnomeSession: "The name org.gnome.SessionManager was not provided by any .service files" 

```

This gives me a top bar with very few icons (but at least I could have the sound back)

```
dgaudin@prometeodg:~$ unity-2d-shell &
[3] 4716
dgaudin@prometeodg:~$ unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.14.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [WARNING] void GnomeSessionClient::slotRegisterClientFinished(QDBusPendingCallWatcher*): Failed to register with GnomeSession: "The name org.gnome.SessionManager was not provided by any .service files" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus-home.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
```

This gives me a left bar with the default icons

```
dgaudin@prometeodg:~$ unity-2d-spread &
[4] 4736
dgaudin@prometeodg:~$ unity-2d-spread: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
unity-2d-spread: [WARNING] Object::connect: No such signal WindowsList::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.14.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-spread: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-spread: [WARNING] Object::connect: No such signal WindowsList::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.14.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-spread: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-spread: [WARNING] Object::connect: No such signal WindowsList::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.14.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-spread: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-spread: [WARNING] Object::connect: No such signal WindowsList::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.14.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-spread: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames
```

This does not do anything.


Maybe this can help ?

---

