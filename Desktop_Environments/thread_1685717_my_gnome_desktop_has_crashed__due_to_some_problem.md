---
title: "my gnome desktop has crashed  due to some problem"
date: 2011-02-11
forum: Desktop Environments
---

### Post by tapas_mishra on 2011-02-11
My Gnome desktop have crashed now due to some problem,
I have tried
```
 dpkg-reconfigure xserver-xorg
``` and
```
 dpkg-reconfigure gdm
```on recovery mode but that did not worked.

```
sudo apt-get install --reinstall ubuntu-desktop
``` at recovery
with networking also tried but did not worked.

I have tried this but I am right now in the same situation and that desktop does not boot.
following is dmesg log
> 
[ 26.883190] type=1505 audit(1297420257.664:5): operation="profile_load" pid=1203 name="/usr/share/gdm/guest-session/Xsession"
[ 26.884764] type=1505 audit(1297420257.664:6): operation="profile_replace" pid=1204 name="/sbin/dhclient3"
[ 26.885417] type=1505 audit(1297420257.664:7): operation="profile_replace" pid=1204 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 26.885763] type=1505 audit(1297420257.664:: operation="profile_replace" pid=1204 name="/usr/lib/connman/scripts/dhclient-script"
[ 26.888549] type=1505 audit(1297420257.664:9): operation="profile_load" pid=1205 name="/usr/bin/evince"
[ 26.896967] type=1505 audit(1297420257.674:10): operation="profile_load" pid=1205 name="/usr/bin/evince-previewer"
[ 26.901980] type=1505 audit(1297420257.684:11): operation="profile_load" pid=1205 name="/usr/bin/evince-thumbnailer"
I also see following in daemon.log
> 
Feb 11 16:00:59 tapas avahi-daemon[1186]: Registering new address record for fe80::74c2:90ff:feb1:b742 on virbr0.*.
Feb 11 16:01:00 tapas gdm-simple-slave[1191]: WARNING: Unable to open session: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success#012
Feb 11 16:01:00 tapas gdm-simple-slave[1191]: WARNING: Could not spawn command: Failed to execute child process "/usr/bin/dbus-launch" (Permission denied)
Feb 11 16:01:00 tapas gdm-simple-slave[1191]: WARNING: Unable to launch D-Bus daemon: Failed to execute child process "/usr/bin/dbus-launch" (Permission denied)
Feb 11 16:01:00 tapas gdm-simple-slave[1191]: WARNING: Could not spawn command: Failed to execute child process "/usr/bin/gnome-session" (Permission denied)
Feb 11 16:01:00 tapas gdm-simple-slave[1191]: WARNING: Could not start command '/usr/bin/gnome-session --autostart=/usr/share/gdm/autostart/LoginWindow/': Failed to exe

following is dpkg.log

> 
2011-02-09 16:34:32 startup packages configure
2011-02-11 15:59:50 startup archives unpack
2011-02-11 15:59:52 upgrade ubuntu-desktop 1.197 1.197
2011-02-11 15:59:52 status half-configured ubuntu-desktop 1.197
2011-02-11 15:59:52 status unpacked ubuntu-desktop 1.197
2011-02-11 15:59:52 status half-installed ubuntu-desktop 1.197
2011-02-11 15:59:53 status half-installed ubuntu-desktop 1.197
2011-02-11 15:59:53 status unpacked ubuntu-desktop 1.197
2011-02-11 15:59:53 status unpacked ubuntu-desktop 1.197
2011-02-11 15:59:54 startup packages configure
2011-02-11 15:59:54 configure ubuntu-desktop 1.197 1.197
2011-02-11 15:59:54 status unpacked ubuntu-desktop 1.197
2011-02-11 15:59:54 status half-configured ubuntu-desktop 1.197
2011-02-11 15:59:54 status installed ubuntu-desktop 1.197
and Xorg.0.log is > 
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event5)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event5"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Integrated_Webcam_1.3M: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Dell WMI hotkeys: Close
(II) UnloadModule: "evdev"
ddxSigGiveUp: Closing log
and here is
/var/log/gdm/\:0.log
> 
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux tkmsr 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=06ecf0b7-ab12-4ada-82dc-d3267d45ad21 ro splash quiet splash
Build Date: 21 July 2010 01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.16.4
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 11 16:00:58 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section. Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) | |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
Using a default monitor configuration.
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
35,2-9 Top
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
If no devices become available, reconfigure udev or disable AutoAddDevices.
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a42:1028:02cf Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf6c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000efe8/8
(--) PCI: (0:0:2:1) 8086:2a43:1028:02cf Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf6b00000/1048576
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
(==) AIGLX enabled
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.1.0
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 2.9.1

(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 2.3.0
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 0.4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 0.0.2
(II) intel(0): Creating default Display subsection in Screen section
"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
(--) intel(0): Chipset: "GM45"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LGD Model: 18b Serial#: 0
(II) intel(0): Year: 2008 Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 31 vert.: 17
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.618 redY: 0.355 greenX: 0.330 greenY: 0.584
(II) intel(0): blueX: 0.145 blueY: 0.094 whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 72.3 MHz Image Size: 310 x 174 mm
(II) intel(0): h_active: 1366 h_sync: 1414 h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) intel(0): v_active: 768 v_sync: 771 v_sync_end 776 v_blanking: 790 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 72.3 MHz Image Size: 310 x 174 mm
(II) intel(0): h_active: 1366 h_sync: 1414 h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) intel(0): v_active: 768 v_sync: 771 v_sync_end 776 v_blanking: 790 v_border: 0
(II) intel(0): X976H<80>140WH1
(II) intel(0): Unknown vendor-specific block 0
(II) intel(0): EDID (in hex):
(II) intel(0): 00ffffffffffff0030e48b0100000000
(II) intel(0): 00120103801f11780a4a059e5b549525
(II) intel(0): 18505400000001010101010101010101
(II) intel(0): 0101010101013e1c56a0500016303020
(II) intel(0): 350036ae100000193e1c56a050001630
(II) intel(0): 3020350036ae10000019000000fe0058
(II) intel(0): 39373648803134305748310a00000000
(II) intel(0): 00ffffffffffffffff01010a20200095
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1366x768"x60.0 72.30 1366 1414 1446 1526 768 771 776 790 -hsync -vsync (47.4 kHz)
(II) intel(0): Modeline "1360x768"x59.8 84.75 1360 1432 1568 1776 768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0 94.50 1024 1072 1168 1376 768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0 78.75 1024 1040 1136 1312 768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1 75.00 1024 1048 1184 1328 768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6 57.28 832 864 928 1152 624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1 56.30 800 832 896 1048 600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2 50.00 800 856 976 1040 600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0 49.50 800 816 896 1056 600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2 36.00 800 824 896 1024 600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0 36.00 640 696 752 832 480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8 31.50 640 664 704 832 480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0 31.50 640 656 720 840 480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0 35.50 720 756 828 936 400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1 31.50 640 672 736 832 400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1 31.50 640 672 736 832 350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DP1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1366x768
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II) solid
(II) copy
(II) composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 361 x 203
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event9)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 2.3.2
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event9"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(II) config/udev: Adding input device Video Bus (/dev/input/event10)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(II) config/udev: Adding input device Integrated_Webcam_1.3M (/dev/input/event6)
(**) Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
(**) Integrated_Webcam_1.3M: always reports core events
(**) Integrated_Webcam_1.3M: Device: "/dev/input/event6"
(II) Integrated_Webcam_1.3M: Found keys
(II) Integrated_Webcam_1.3M: Configuring as keyboard
(II) XINPUT: Adding extended input device "Integrated_Webcam_1.3M" (type: KEYBOARD)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event7)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event7"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.2.2
(II) Synaptics touchpad driver version 1.2.2
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
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event5)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event5"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(II) Video Bus: Close
(II) Video Bus: Close
(II) Power Button: Close
(II) Sleep Button: Close
(II) Integrated_Webcam_1.3M: Close
(II) AT Translated Set 2 keyboard: Close
(II) PS/2 Mouse: Close
(II) Macintosh mouse button emulation: Close
(II) Dell WMI hotkeys: Close
ddxSigGiveUp: Closing log
any pointers here.

---

