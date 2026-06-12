---
title: "XORG error 11"
date: 2009-04-03
forum: General Help
---

### Post by PurposeOfReason on 2009-04-03
I'm not sure what is wront, I've tried nvidia, vesa, and nv drivers. Disabling and enabling hotpluging.

```
X.Org X Server 1.5.3
Release Date: 5 November 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.27-ARCH x86_64 
Current Operating System: Linux gordon 2.6.28-ARCH #1 SMP PREEMPT Sun Feb 8 09:47:26 UTC 2009 x86_64
Build Date: 17 December 2008  10:46:49PM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr  2 14:31:21 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(**) Option "AutoAddDevices" "False"
(**) Not automatically adding devices
(==) Automatically enabling devices
(==) Including the default font path /usr/share/fonts/misc,/usr/share/fonts/100dpi:unscaled,/usr/share/fonts/75dpi:unscaled,/usr/share/fonts/TTF,/usr/share/fonts/Type1.
(**) FontPath set to:
    /usr/share/fonts/misc,
    /usr/share/fonts/100dpi:unscaled,
    /usr/share/fonts/75dpi:unscaled,
    /usr/share/fonts/TTF,
    /usr/share/fonts/misc,
    /usr/share/fonts/100dpi:unscaled,
    /usr/share/fonts/75dpi:unscaled,
    /usr/share/fonts/TTF,
    /usr/share/fonts/Type1
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x7b54e0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI: (0@0:3:3) nVidia Corporation MCP73 Co-processor rev 162, Mem @ 0xeff00000/524288
(--) PCI:*(0@0:16:0) nVidia Corporation GeForce 7100/nForce 630i rev 162, Mem @ 0xed000000/16777216, 0xd0000000/268435456, 0xee000000/16777216, BIOS @ 0x????????/131072
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"

(WW) Warning, couldn't open module record
(II) UnloadModule: "record"
(EE) Failed to load module "record" (module does not exist, 0)
(II) LoadModule: "xtrap"

(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
    compiled for 1.5.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DEC-XTRAP
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4ed8e6]
1: /usr/bin/X(xf86SigHandler+0x39) [0x496739]
2: /lib/libc.so.6 [0x7fc468682150]
3: /lib/ld-linux-x86-64.so.2 [0x7fc46a3c5761]
4: /lib/ld-linux-x86-64.so.2 [0x7fc46a3cc96b]
5: /lib/ld-linux-x86-64.so.2 [0x7fc46a3c83b6]
6: /lib/ld-linux-x86-64.so.2 [0x7fc46a3cc22b]
7: /lib/libdl.so.2 [0x7fc469fb1f5b]
8: /lib/ld-linux-x86-64.so.2 [0x7fc46a3c83b6]
9: /lib/libdl.so.2 [0x7fc469fb230c]
10: /lib/libdl.so.2(dlopen+0x31) [0x7fc469fb1ec1]
11: /usr/bin/X(DLLoadModule+0x1c) [0x46d53c]
12: /usr/bin/X(LoaderOpen+0x18c) [0x46b11c]
13: /usr/bin/X [0x46c88a]
14: /usr/bin/X(LoadModule+0x24) [0x46d2d4]
15: /usr/bin/X(xf86LoadModules+0xa9) [0x467f49]
16: /usr/bin/X(InitOutput+0x4b4) [0x469ea4]
17: /usr/bin/X(main+0x286) [0x4334c6]
18: /lib/libc.so.6(__libc_start_main+0xe6) [0x7fc46866e546]
19: /usr/bin/X [0x432a79]

Fatal server error:
Caught signal 11.  Server aborting
```

---

### Post by Dejai on 2009-04-03
I noticed that this problem is actually with ARCH Linux: [http://bbs.archlinux.org/viewtopic.php?id=68978](http://bbs.archlinux.org/viewtopic.php?id=68978) there is not much I can do to help you except I suggest that you check your configuration files.  Maybe you should find out the definition of Xorg error 11 and see where to go from there. Anyway sorry I couldn't have been of more help.

---

