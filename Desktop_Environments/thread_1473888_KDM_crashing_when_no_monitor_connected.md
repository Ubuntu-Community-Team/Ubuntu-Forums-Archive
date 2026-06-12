---
title: "KDM crashing when no monitor connected"
date: 2010-05-05
forum: Desktop Environments
---

### Post by F@Ze on 2010-05-05
I did a fresh install of Kubuntu 10.4 (Lucid). With my monitor connected everything seems fine. I have a nVidia onboard vga card which works correctly.

I installed x11vnc because I will be using the system primary remotely. x11vnc started by adding it in the Autostart folder. 
This was all working correctly.

Now I moved the system to the place where it will be working (with no display) and the x11vnc didn't come up.
I removed the x11 from autostart, but still no luck. It seems KDM isn't booting at all and I think because there is no display.

When I look at Xorg.0.log I see two important messages:
1. No display found (and that's correct)
2. Caught signal 11 (Segmentation fault). Server aborting

Here the (last) lines from the log:
```
(--) NOUVEAU(0): Chipset: "NVIDIA NV4e"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): Output DVI-D-1 has no monitor section
(II) NOUVEAU(0): Output TV-1 has no monitor section
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): EDID for output DVI-D-1
(II) NOUVEAU(0): EDID for output TV-1

(II) NOUVEAU(0): Output VGA-1 disconnected
(II) NOUVEAU(0): Output DVI-D-1 disconnected
(II) NOUVEAU(0): Output TV-1 disconnected
(WW) NOUVEAU(0): No outputs definitely connected, trying again...
(II) NOUVEAU(0): Output VGA-1 disconnected
(II) NOUVEAU(0): Output DVI-D-1 disconnected
(II) NOUVEAU(0): Output TV-1 disconnected
(WW) NOUVEAU(0): Unable to find initial modes
(--) NOUVEAU(0): Virtual size is 0x0 (pitch 0)
(==) NOUVEAU(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.5.0
        ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7f199af03000+0xf8f0) [0x7f199af128f0]
3: /usr/bin/X (xf86InitViewport+0x4b) [0x5247fb]
4: /usr/bin/X (InitOutput+0xb2d) [0x473f8d]
5: /usr/bin/X (0x400000+0x26005) [0x426005]
6: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f1999bfbc4d]
7: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address 0x24

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
```

Any help would be appreciated!

---

### Post by Zorael on 2010-05-06
See if there's any other interesting output in **/var/log/kdm.log**. This sounds like it warrants a bug report.

---

### Post by F@Ze on 2010-05-06
Here the output of kdm.log:

```
file(s) it is logged. PAM logs messages related to authentication to authpriv.*.
********************************************************************************


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux HTPC 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=17fbef15-b6aa-4a78-b539-dc14274338da ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  6 21:20:12 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7ff0121f9000+0xf8f0) [0x7ff0122088f0]
3: /usr/bin/X (xf86InitViewport+0x4b) [0x5247fb]
4: /usr/bin/X (InitOutput+0xb2d) [0x473f8d]
5: /usr/bin/X (0x400000+0x26005) [0x426005]
6: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7ff010ef1c4d]
7: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address 0x24

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
md5sum: /etc/X11/xorg.conf: No such file or directory
/etc/gdm/failsafeXServer: line 141: /var/log/gdm/failsafe.log: No such file or directory
Warning:  Cannot write to /var/log/gdm/failsafe.log
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X  -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux HTPC 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=17fbef15-b6aa-4a78-b539-dc14274338da ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu May  6 21:20:12 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) VESA: Kernel modesetting driver in use, refusing to load
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.

 ddxSigGiveUp: Closing log


```

I also tried sudo Xorg -configure
which gives me (last lines):
```
List of video drivers:
        rendition
        mga
        neomagic
        apm
        nouveau
        mach64
        ark
        nv
        i128
        s3virge
        tseng
        openchrome
        chips
        sisusb
        s3
        sis
        vmware
        trident
        v4l
        voodoo
        cirrus
        radeon
        tdfx
        intel
        savage
        r128
        ati
        siliconmotion
        fbdev
        vesa
(++) Using config file: "/home/me/xorg.conf.new"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) [drm] No DRICreatePCIBusID symbol
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log

```
I tried to copy xorg.conf.new to /etc/X11/xorg.conf.
when running the config said something about not being able to write to /var/log/gdm/(something). So I created that directory.
The kdm.log now looks like:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux HTPC 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=17fbef15-b6aa-4a78-b539-dc14274338da ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  6 21:44:09 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7f5543afa000+0xf8f0) [0x7f5543b098f0]
3: /usr/bin/X (xf86InitViewport+0x4b) [0x5247fb]
4: /usr/bin/X (InitOutput+0xb2d) [0x473f8d]
5: /usr/bin/X (0x400000+0x26005) [0x426005]
6: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f55427f2c4d]
7: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address 0x24

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X  -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux HTPC 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=17fbef15-b6aa-4a78-b539-dc14274338da ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu May  6 21:44:10 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) VESA: Kernel modesetting driver in use, refusing to load
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.

 ddxSigGiveUp: Closing log

```

And to make it complete: the xorg.conf created by Xorg --configure:
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "dri2"
        Load  "dri"
        Load  "glx"
        Load  "extmod"
        Load  "dbe"
        Load  "record"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "HWcursor"                  # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "EXAPixmaps"                # [<bool>]
        Identifier  "Card0"
        Driver      "nouveau"
        VendorName  "nVidia Corporation"
        BoardName   "C51PV [GeForce 6150]"
        BusID       "PCI:0:5:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```
:(
Can I force the display somehow to the tv-out port?
I already thought about buying a tv to connect to the pc.. but that's not economically ok ;)

---

### Post by F@Ze on 2010-05-07
Sorry to bump this, but I really don't know how to solve this. I'm sure I'm not the first one with this problem. The Geforce 6150 is not that rare and running a linux pc without a monitor is not that special isn't it? ;)

---

### Post by krunge on 2010-05-07
What happens if you take the xorg.conf that you pasted above and are now using and change "nouveau" to "vesa"?  Since there is no monitor, this shouldn't make any difference. Actually the one difference it will probably make is to  speedup up the x11vnc response.

You may need to create a bogus monitor section in xorg.conf, e.g.:
[INDENT][http://ubuntuforums.org/showthread.php?t=1388613](http://ubuntuforums.org/showthread.php?t=1388613)[/INDENT]
and similar posts.

---

### Post by F@Ze on 2010-05-09
Thanks for the reply. I figured to work around it myself and tested the suggested solution afterwards.

What I did to fix it:
[LIST]
[*]Because the errors looked as they were related to the nouveau
 driver I removed it / blacklisted it. My previous ubuntu had no problems and I couldn't replace the xorg.conf with the old one, because it used the nvidia driver.
[*]I installed the (64 bit) nvidia driver from their website (NVIDIA-Linux-x86_64-195.36.24-pkg2.run). It wasn't that easy to get it to work, needed a lot of dependencies and was not clear which ones. I think installing the build-essentials / g++ / gcc did the job.
[*]Now I had new config file with the nvidia driver... but: still the same problem. I merged it with the config file from my previous installation, but still the same problem : no screens found
[*]Now what did the job: one row forcing to use the TV output!: Option "ConnectedMonitor" "TV"
[/LIST]

This is my current (working) xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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

        # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"

        # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
    Option         "TVStandard" "PAL-B"
    Option         "TVOutFormat" "SVIDEO"
    Option         "NoLogo" "True"
    Option "ConnectedMonitor" "TV"
    BusID          "PCI:0:5:0"
    Screen          0
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 1600x900 +0+0; CRT: 640x480 +0+0"
# Removed Option "metamodes" "1600x900 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1440x900 +0+0"
    SubSection     "Display"
        Depth       16
    EndSubSection
EndSection

```

The solution you provided also worked and is perfect for only using the pc for remote work. I on the other hand would like to connect my tv once in a while and use it as htpc and/or play a game. I think it's then best to use the nvidia drivers.

---

