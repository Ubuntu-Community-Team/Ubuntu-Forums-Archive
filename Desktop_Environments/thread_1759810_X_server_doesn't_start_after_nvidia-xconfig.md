---
title: "X server doesn't start after nvidia-xconfig"
date: 2011-05-16
forum: Desktop Environments
---

### Post by M2-player on 2011-05-16
When I start Live CD, Unity is working.
When I installed Ubuntu, Unity isn't working.
NVIDIA accelerated graphics Driver is activated but not currently in use.
I ran *sudo nvidia-xconfig*
then I restarted X server by *sudo** /etc/init.d/gdm restart*
but after that X server was not able to start.
Here's a log from /var/log/Xorg.0.log :

```
[   110.712] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   110.718] X Protocol Version 11, Revision 0
[   110.719] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   110.721] Current Operating System: Linux M2-PC 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[   110.722] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=af9a3adc-44a3-4d90-be1a-83202c746160 ro single
[   110.723] Build Date: 19 April 2011  03:40:45PM
[   110.724] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[   110.725] Current version of pixman: 0.20.2
[   110.726]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   110.728] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   110.731] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May 16 09:13:15 2011
[   110.733] (==) Using config file: "/etc/X11/xorg.conf"
[   110.734] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   110.735] (==) ServerLayout "Layout0"
[   110.735] (**) |-->Screen "Screen0" (0)
[   110.735] (**) |   |-->Monitor "Monitor0"
[   110.735] (**) |   |-->Device "Device0"
[   110.735] (**) |-->Input Device "Keyboard0"
[   110.735] (**) |-->Input Device "Mouse0"
[   110.735] (==) Automatically adding devices
[   110.735] (==) Automatically enabling devices
[   110.735] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   110.735] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   110.735] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   110.735] (WW) Disabling Keyboard0
[   110.735] (WW) Disabling Mouse0
[   110.735] (II) Loader magic: 0x7e0280
[   110.735] (II) Module ABI versions:
[   110.735]     X.Org ANSI C Emulation: 0.4
[   110.736]     X.Org Video Driver: 10.0
[   110.736]     X.Org XInput driver : 12.3
[   110.736]     X.Org Server Extension : 5.0
[   110.736] (--) PCI:*(0:0:2:0) 8086:0046:152d:0813 rev 2, Mem @ 0xd1400000/4194304, 0xc0000000/268435456, I/O @ 0x00005050/8
[   110.736] (--) PCI: (0:1:0:0) 10de:0caf:152d:0813 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[   110.736] (II) Open ACPI successful (/var/run/acpid.socket)
[   110.736] (II) LoadModule: "extmod"
[   110.737] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   110.737] (II) Module extmod: vendor="X.Org Foundation"
[   110.737]     compiled for 1.10.1, module version = 1.0.0
[   110.737]     Module class: X.Org Server Extension
[   110.737]     ABI class: X.Org Server Extension, version 5.0
[   110.737] (II) Loading extension MIT-SCREEN-SAVER
[   110.737] (II) Loading extension XFree86-VidModeExtension
[   110.737] (II) Loading extension XFree86-DGA
[   110.737] (II) Loading extension DPMS
[   110.737] (II) Loading extension XVideo
[   110.737] (II) Loading extension XVideo-MotionCompensation
[   110.737] (II) Loading extension X-Resource
[   110.737] (II) LoadModule: "dbe"
[   110.737] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   110.737] (II) Module dbe: vendor="X.Org Foundation"
[   110.737]     compiled for 1.10.1, module version = 1.0.0
[   110.737]     Module class: X.Org Server Extension
[   110.737]     ABI class: X.Org Server Extension, version 5.0
[   110.737] (II) Loading extension DOUBLE-BUFFER
[   110.737] (II) LoadModule: "glx"
[   110.737] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   110.745] (II) Module glx: vendor="NVIDIA Corporation"
[   110.745]     compiled for 4.0.2, module version = 1.0.0
[   110.745]     Module class: X.Org Server Extension
[   110.745] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[   110.745] (II) Loading extension GLX
[   110.745] (II) LoadModule: "record"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   110.746] (II) Module record: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.13.0
[   110.746]     Module class: X.Org Server Extension
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension RECORD
[   110.746] (II) LoadModule: "dri"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   110.746] (II) Module dri: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.0.0
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension XFree86-DRI
[   110.746] (II) LoadModule: "dri2"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   110.746] (II) Module dri2: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.2.0
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension DRI2
[   110.746] (II) LoadModule: "nvidia"
[   110.746] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   110.747] (II) Module nvidia: vendor="NVIDIA Corporation"
[   110.747]     compiled for 4.0.2, module version = 1.0.0
[   110.747]     Module class: X.Org Video Driver
[   110.747] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[   110.747] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   110.747] (--) using VT number 7

[   110.750] (EE) No devices detected.
[   110.750] 
Fatal server error:
[   110.750] no screens found
[   110.750] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   110.750] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   110.750] 

```I have actually 2 graphics - NVidia and Intel (cause my CPU is Intel i5 ).
Ubuntu 11.04.

---

### Post by wildmanne39 on 2011-05-16
> **M2-player said:**
> When I start Live CD, Unity is working.
When I installed Ubuntu, Unity isn't working.
NVIDIA accelerated graphics Driver is activated but not currently in use.
I ran *sudo nvidia-xconfig*
then I restarted X server by *sudo** /etc/init.d/gdm restart*
but after that X server was not able to start.
Here's a log from /var/log/Xorg.0.log :

```
[   110.712] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   110.718] X Protocol Version 11, Revision 0
[   110.719] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   110.721] Current Operating System: Linux M2-PC 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[   110.722] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=af9a3adc-44a3-4d90-be1a-83202c746160 ro single
[   110.723] Build Date: 19 April 2011  03:40:45PM
[   110.724] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[   110.725] Current version of pixman: 0.20.2
[   110.726]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   110.728] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   110.731] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May 16 09:13:15 2011
[   110.733] (==) Using config file: "/etc/X11/xorg.conf"
[   110.734] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   110.735] (==) ServerLayout "Layout0"
[   110.735] (**) |-->Screen "Screen0" (0)
[   110.735] (**) |   |-->Monitor "Monitor0"
[   110.735] (**) |   |-->Device "Device0"
[   110.735] (**) |-->Input Device "Keyboard0"
[   110.735] (**) |-->Input Device "Mouse0"
[   110.735] (==) Automatically adding devices
[   110.735] (==) Automatically enabling devices
[   110.735] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   110.735] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   110.735] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   110.735] (WW) Disabling Keyboard0
[   110.735] (WW) Disabling Mouse0
[   110.735] (II) Loader magic: 0x7e0280
[   110.735] (II) Module ABI versions:
[   110.735]     X.Org ANSI C Emulation: 0.4
[   110.736]     X.Org Video Driver: 10.0
[   110.736]     X.Org XInput driver : 12.3
[   110.736]     X.Org Server Extension : 5.0
[   110.736] (--) PCI:*(0:0:2:0) 8086:0046:152d:0813 rev 2, Mem @ 0xd1400000/4194304, 0xc0000000/268435456, I/O @ 0x00005050/8
[   110.736] (--) PCI: (0:1:0:0) 10de:0caf:152d:0813 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[   110.736] (II) Open ACPI successful (/var/run/acpid.socket)
[   110.736] (II) LoadModule: "extmod"
[   110.737] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   110.737] (II) Module extmod: vendor="X.Org Foundation"
[   110.737]     compiled for 1.10.1, module version = 1.0.0
[   110.737]     Module class: X.Org Server Extension
[   110.737]     ABI class: X.Org Server Extension, version 5.0
[   110.737] (II) Loading extension MIT-SCREEN-SAVER
[   110.737] (II) Loading extension XFree86-VidModeExtension
[   110.737] (II) Loading extension XFree86-DGA
[   110.737] (II) Loading extension DPMS
[   110.737] (II) Loading extension XVideo
[   110.737] (II) Loading extension XVideo-MotionCompensation
[   110.737] (II) Loading extension X-Resource
[   110.737] (II) LoadModule: "dbe"
[   110.737] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   110.737] (II) Module dbe: vendor="X.Org Foundation"
[   110.737]     compiled for 1.10.1, module version = 1.0.0
[   110.737]     Module class: X.Org Server Extension
[   110.737]     ABI class: X.Org Server Extension, version 5.0
[   110.737] (II) Loading extension DOUBLE-BUFFER
[   110.737] (II) LoadModule: "glx"
[   110.737] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   110.745] (II) Module glx: vendor="NVIDIA Corporation"
[   110.745]     compiled for 4.0.2, module version = 1.0.0
[   110.745]     Module class: X.Org Server Extension
[   110.745] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[   110.745] (II) Loading extension GLX
[   110.745] (II) LoadModule: "record"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   110.746] (II) Module record: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.13.0
[   110.746]     Module class: X.Org Server Extension
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension RECORD
[   110.746] (II) LoadModule: "dri"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   110.746] (II) Module dri: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.0.0
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension XFree86-DRI
[   110.746] (II) LoadModule: "dri2"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   110.746] (II) Module dri2: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.2.0
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension DRI2
[   110.746] (II) LoadModule: "nvidia"
[   110.746] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   110.747] (II) Module nvidia: vendor="NVIDIA Corporation"
[   110.747]     compiled for 4.0.2, module version = 1.0.0
[   110.747]     Module class: X.Org Video Driver
[   110.747] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[   110.747] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   110.747] (--) using VT number 7

[   110.750] (EE) No devices detected.
[   110.750] 
Fatal server error:
[   110.750] no screens found
[   110.750] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   110.750] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   110.750] 

```I have actually 2 graphics - NVidia and Intel (cause my CPU is Intel i5 ).
Ubuntu 11.04.
Hi, as far as the nividia card not in use, that is a bug and actually if you activated it, it is in use it just does not show it, so if you manually changed your x org server file just restore it with the back up you created before you changed the settings.:)

---

### Post by wildmanne39 on 2011-05-16
> **M2-player said:**
> When I start Live CD, Unity is working.
When I installed Ubuntu, Unity isn't working.
NVIDIA accelerated graphics Driver is activated but not currently in use.
I ran *sudo nvidia-xconfig*
then I restarted X server by *sudo** /etc/init.d/gdm restart*
but after that X server was not able to start.
Here's a log from /var/log/Xorg.0.log :

```
[   110.712] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   110.718] X Protocol Version 11, Revision 0
[   110.719] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   110.721] Current Operating System: Linux M2-PC 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[   110.722] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=af9a3adc-44a3-4d90-be1a-83202c746160 ro single
[   110.723] Build Date: 19 April 2011  03:40:45PM
[   110.724] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[   110.725] Current version of pixman: 0.20.2
[   110.726]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   110.728] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   110.731] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May 16 09:13:15 2011
[   110.733] (==) Using config file: "/etc/X11/xorg.conf"
[   110.734] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   110.735] (==) ServerLayout "Layout0"
[   110.735] (**) |-->Screen "Screen0" (0)
[   110.735] (**) |   |-->Monitor "Monitor0"
[   110.735] (**) |   |-->Device "Device0"
[   110.735] (**) |-->Input Device "Keyboard0"
[   110.735] (**) |-->Input Device "Mouse0"
[   110.735] (==) Automatically adding devices
[   110.735] (==) Automatically enabling devices
[   110.735] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   110.735]     Entry deleted from font path.
[   110.735] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   110.735] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   110.735] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   110.735] (WW) Disabling Keyboard0
[   110.735] (WW) Disabling Mouse0
[   110.735] (II) Loader magic: 0x7e0280
[   110.735] (II) Module ABI versions:
[   110.735]     X.Org ANSI C Emulation: 0.4
[   110.736]     X.Org Video Driver: 10.0
[   110.736]     X.Org XInput driver : 12.3
[   110.736]     X.Org Server Extension : 5.0
[   110.736] (--) PCI:*(0:0:2:0) 8086:0046:152d:0813 rev 2, Mem @ 0xd1400000/4194304, 0xc0000000/268435456, I/O @ 0x00005050/8
[   110.736] (--) PCI: (0:1:0:0) 10de:0caf:152d:0813 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[   110.736] (II) Open ACPI successful (/var/run/acpid.socket)
[   110.736] (II) LoadModule: "extmod"
[   110.737] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   110.737] (II) Module extmod: vendor="X.Org Foundation"
[   110.737]     compiled for 1.10.1, module version = 1.0.0
[   110.737]     Module class: X.Org Server Extension
[   110.737]     ABI class: X.Org Server Extension, version 5.0
[   110.737] (II) Loading extension MIT-SCREEN-SAVER
[   110.737] (II) Loading extension XFree86-VidModeExtension
[   110.737] (II) Loading extension XFree86-DGA
[   110.737] (II) Loading extension DPMS
[   110.737] (II) Loading extension XVideo
[   110.737] (II) Loading extension XVideo-MotionCompensation
[   110.737] (II) Loading extension X-Resource
[   110.737] (II) LoadModule: "dbe"
[   110.737] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   110.737] (II) Module dbe: vendor="X.Org Foundation"
[   110.737]     compiled for 1.10.1, module version = 1.0.0
[   110.737]     Module class: X.Org Server Extension
[   110.737]     ABI class: X.Org Server Extension, version 5.0
[   110.737] (II) Loading extension DOUBLE-BUFFER
[   110.737] (II) LoadModule: "glx"
[   110.737] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   110.745] (II) Module glx: vendor="NVIDIA Corporation"
[   110.745]     compiled for 4.0.2, module version = 1.0.0
[   110.745]     Module class: X.Org Server Extension
[   110.745] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[   110.745] (II) Loading extension GLX
[   110.745] (II) LoadModule: "record"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   110.746] (II) Module record: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.13.0
[   110.746]     Module class: X.Org Server Extension
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension RECORD
[   110.746] (II) LoadModule: "dri"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   110.746] (II) Module dri: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.0.0
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension XFree86-DRI
[   110.746] (II) LoadModule: "dri2"
[   110.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   110.746] (II) Module dri2: vendor="X.Org Foundation"
[   110.746]     compiled for 1.10.1, module version = 1.2.0
[   110.746]     ABI class: X.Org Server Extension, version 5.0
[   110.746] (II) Loading extension DRI2
[   110.746] (II) LoadModule: "nvidia"
[   110.746] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   110.747] (II) Module nvidia: vendor="NVIDIA Corporation"
[   110.747]     compiled for 4.0.2, module version = 1.0.0
[   110.747]     Module class: X.Org Video Driver
[   110.747] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[   110.747] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   110.747] (--) using VT number 7

[   110.750] (EE) No devices detected.
[   110.750] 
Fatal server error:
[   110.750] no screens found
[   110.750] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   110.750] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   110.750] 

```I have actually 2 graphics - NVidia and Intel (cause my CPU is Intel i5 ).
Ubuntu 11.04.

HI, have you also tried to restart ubuntu a couple of times because if it does not start right the first time, it has a feature that tries to fix the problem so it will start the next time, and the command you used for restarting x I am not sure that is the right one with unity.

---

### Post by Krytarik on 2011-05-17
Try reinstalling the driver, "nvidia-current":
```

sudo apt-get update
sudo apt-get install --reinstall nvidia-current
```
If that doesn't doesn't fix it,
- rename your xorg.conf
- restart GDM
- install/activate "nvidia-173" through "Additional Drivers"

Greetings.

---

### Post by M2-player on 2011-05-21
Thanks a lot to all. Renaming of xorg.conf file worked and desktop is back.

Can I ask you a  one more question? Now I have the same problem as I mentioned in first post.
I don't know how to make NVidia driver to work.
This is how my Additionl Drivers looks: [http://i52.tinypic.com/161fcwz.png](http://i52.tinypic.com/161fcwz.png)
If I would proceed with the same steps as I did before, the X server should be broken again.

---

### Post by shnplr on 2011-05-21
Hi,
I had the same problem starting unity which worked after I installed the nvidia-current driver and created a new /etc/X11/xorg.conf with "sudo nvidia-xconfig", and then tweaked dual monitor with "sudo nvidia-settings".

The nvidia-settings didn't work (command not found) when I also tried the 173 driver.

After this I notice that the device reports as not in use, but can accept that as a bug I guess.

I also notice now that the System Settings --> Monitors no longer shows my 2 monitors. It now just shows one monitor called "Unknown" - my ~/.config/monitors.xml still contains the correct data for both monitors.

I also notice whereas before xrandr displayed a whole heap of interesting data, now just shows a few lines with some invalid minimum resolutions.  Is this part of the same bug, or is there some other way to get Unity working with xrandr without installing the proprietary nvidia driver? - the difference in xrandr output before and after installing the Nvidia driver is significant.

Oh, and I also edited the xorg.conf to add the RandRRotation option - that got rid of the "Rotation not supported" error in the Monitors app but didn't stop the "Unknown monitor".  Perhaps the Monitors app is redundant after installing proprietary nvidia driver?

For now I've uninstalled the Nvidia driver and using gnome classic - does this seem like a sensible approach until whatever bugs are finally resolved?

---

### Post by Krytarik on 2011-05-21
There is a bug regarding the "not in use" statement of the jockey, aka "Additional Drivers":
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

The driver is usually being run fine, just check the output of:
```
lshw -c video
```Also, although the "nvidia-173" driver isn't listed in the jockey in the screenshot, you should try it if you are still having issues with "nvidia-current".

To install it manually:
```
sudo apt-get install nvidia-173
```Regarding the proprietary Nvidia driver and xrandr, they seem to be not working well together, the functionality of xrandr is extremely limited when the proprietary Nvidia driver is running.

---

### Post by M2-player on 2011-05-25
I tried nvidia-173 but there was problem to run Ubuntu, so I activeted nvidia-curret again. 

The output of *sudo lshw -c video* is:

```
  *-display               
       description: VGA compatible controller
       product: GT215 [GeForce GT 335M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:d1000000-d107ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:5050(size=8)
```Anyway, thanks for answers and for a link on launchpad. I have my eyes on it.

---

### Post by kamiller42 on 2011-10-21
I am experiencing a problem very similar, if not the same, as the one described in this thread.

I am using Ubuntu 11.10 64-bit on a Dell XPS 17 with a Geforce GT 555M. I have tried the installing the driver from Additional Drivers and the drivers from the nVidia site with the same results. X server does not start upon reboot. I have to rename xorg.conf or delete it to boot into Ubuntu. Here is all the information I think it needed to troubleshoot. 

Your help is greatly appreciated.

This xorg.conf nvidia-xconfig creates and causes X server to not boot.
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 280.13  (buildmeister@swio-display-x86-rhel47-03.nvidia.com)  Wed Jul 27 17:15:58 PDT 2011


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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```xorg.log from a failed boot...
```

[    31.803] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    31.803] X Protocol Version 11, Revision 0
[    31.803] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    31.803] Current Operating System: Linux Isidore2011 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    31.803] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=202dfc92-b604-4fc2-a6d0-75b2f78ca939 ro recovery nomodeset
[    31.804] Build Date: 13 October 2011  05:44:30PM
[    31.804] xorg-server 2:1.10.4-1ubuntu4.1 (For technical support please see http://www.ubuntu.com/support) 
[    31.804] Current version of pixman: 0.22.2
[    31.804]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    31.804] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.804] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 21 21:19:23 2011
[    31.804] (==) Using config file: "/etc/X11/xorg.conf"
[    31.804] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.804] (==) ServerLayout "Layout0"
[    31.804] (**) |-->Screen "Screen0" (0)
[    31.804] (**) |   |-->Monitor "Monitor0"
[    31.804] (**) |   |-->Device "Device0"
[    31.804] (**) |-->Input Device "Keyboard0"
[    31.804] (**) |-->Input Device "Mouse0"
[    31.804] (==) Automatically adding devices
[    31.804] (==) Automatically enabling devices
[    31.804] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.804]     Entry deleted from font path.
[    31.804] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.804]     Entry deleted from font path.
[    31.804] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.804]     Entry deleted from font path.
[    31.804] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.804]     Entry deleted from font path.
[    31.804] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.804]     Entry deleted from font path.
[    31.804] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    31.804] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.804] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    31.804] (WW) Disabling Keyboard0
[    31.804] (WW) Disabling Mouse0
[    31.804] (II) Loader magic: 0x7e0220
[    31.804] (II) Module ABI versions:
[    31.804]     X.Org ANSI C Emulation: 0.4
[    31.804]     X.Org Video Driver: 10.0
[    31.804]     X.Org XInput driver : 12.3
[    31.804]     X.Org Server Extension : 5.0
[    31.805] (--) PCI:*(0:0:2:0) 8086:0126:1028:04b8 rev 9, Mem @ 0xf2400000/4194304, 0xe0000000/268435456, I/O @ 0x00005000/64
[    31.805] (--) PCI: (0:1:0:0) 10de:0dcd:1028:04b8 rev 161, Mem @ 0xf0000000/33554432, 0xc0000000/268435456, 0xd0000000/67108864, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    31.805] (II) Open ACPI successful (/var/run/acpid.socket)
[    31.805] (II) LoadModule: "extmod"
[    31.805] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    31.805] (II) Module extmod: vendor="X.Org Foundation"
[    31.805]     compiled for 1.10.4, module version = 1.0.0
[    31.805]     Module class: X.Org Server Extension
[    31.805]     ABI class: X.Org Server Extension, version 5.0
[    31.805] (II) Loading extension MIT-SCREEN-SAVER
[    31.805] (II) Loading extension XFree86-VidModeExtension
[    31.805] (II) Loading extension XFree86-DGA
[    31.805] (II) Loading extension DPMS
[    31.805] (II) Loading extension XVideo
[    31.805] (II) Loading extension XVideo-MotionCompensation
[    31.805] (II) Loading extension X-Resource
[    31.805] (II) LoadModule: "dbe"
[    31.806] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    31.806] (II) Module dbe: vendor="X.Org Foundation"
[    31.806]     compiled for 1.10.4, module version = 1.0.0
[    31.806]     Module class: X.Org Server Extension
[    31.806]     ABI class: X.Org Server Extension, version 5.0
[    31.806] (II) Loading extension DOUBLE-BUFFER
[    31.806] (II) LoadModule: "glx"
[    31.806] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    31.810] (II) Module glx: vendor="NVIDIA Corporation"
[    31.810]     compiled for 4.0.2, module version = 1.0.0
[    31.810]     Module class: X.Org Server Extension
[    31.810] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[    31.810] (II) Loading extension GLX
[    31.810] (II) LoadModule: "record"
[    31.810] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    31.811] (II) Module record: vendor="X.Org Foundation"
[    31.811]     compiled for 1.10.4, module version = 1.13.0
[    31.811]     Module class: X.Org Server Extension
[    31.811]     ABI class: X.Org Server Extension, version 5.0
[    31.811] (II) Loading extension RECORD
[    31.811] (II) LoadModule: "dri"
[    31.811] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    31.811] (II) Module dri: vendor="X.Org Foundation"
[    31.811]     compiled for 1.10.4, module version = 1.0.0
[    31.811]     ABI class: X.Org Server Extension, version 5.0
[    31.811] (II) Loading extension XFree86-DRI
[    31.811] (II) LoadModule: "dri2"
[    31.811] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    31.811] (II) Module dri2: vendor="X.Org Foundation"
[    31.811]     compiled for 1.10.4, module version = 1.2.0
[    31.811]     ABI class: X.Org Server Extension, version 5.0
[    31.811] (II) Loading extension DRI2
[    31.811] (II) LoadModule: "nvidia"
[    31.811] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    32.117] (II) Module nvidia: vendor="NVIDIA Corporation"
[    32.210]     compiled for 4.0.2, module version = 1.0.0
[    32.210]     Module class: X.Org Video Driver
[    32.372] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[    32.372] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    32.373] (++) using VT number 7

[    32.374] (EE) No devices detected.
[    32.374] 
Fatal server error:
[    32.374] no screens found
[    32.374] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    32.374] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    32.374] 

```Output from lshw -c video
```

  *-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 555M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f0000000-f1ffffff memory:c0000000-cfffffff memory:d0000000-d3ffffff ioport:4000(size=128) memory:f2000000-f207ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:53 memory:f2400000-f27fffff memory:e0000000-efffffff ioport:5000(size=64)

```Ubuntu system info reports the following in System Info:

This is the output of unity_support_test -p
```

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: unable to create the OpenGL context

```

Overview/Graphics: Unknown
Graphics/Driver: Unknown 

When Ubuntu loads, it has no 3d support, so it runs unity2d only.

---

### Post by kamiller42 on 2011-10-22
Never mind. I have learned I have an Optimus system and all the lovely issues that come with it. I am now using the new Bumblebee and now I have unity3d. Now, I am a little torn between trying Ironhide or staying with Bumblebee.

---

### Post by Corvair on 2011-11-09
I did as stated by wildmannee39, that is, I ran sudo nvidia-xconfig
then I restarted X server by sudo /etc/init.d/gdm restart
and after that X server was  able to start.

Thank you this was a great help for me.

---

