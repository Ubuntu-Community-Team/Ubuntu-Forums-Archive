---
title: "Weird crash in Lubuntu"
date: 2014-03-30
forum: Desktop Environments
---

### Post by Tar_Ni on 2014-03-30
Hi,

I had a weird crash in Lubuntu, I was browsing the net and then all off the sudden a black screen appeared with something like : ''GPU locked out'' and other things like ''computer rebooting now!'' But the computer was stuck on this black page anyway so I had to manually reboot it.

That was strange, never had problem with Lubuntu 13.10 so far..

Does anyone have a clue what it may be? Hardware problem? my computer is an Intel pentium 4 and so is aging..

---

### Post by kc1di on 2014-03-30
a couple things come to mind , bad ram being one of them, do a memory check overnight some night see if it reveals anything. 

Other possibility is a flash problem which I seen do something similar in the past.  Look in /var logs see if they reveal anything. 
/var/crash would be one place to look. It may tell you exactly what crashed.

---

### Post by Tar_Ni on 2014-03-30
Hi kc1di,

I've located the crash report in /var/crash it is: _usr_bin_Xorg.0.crash

But I don't have access to it. I do not have the permission to open it.

---

### Post by ajgreeny on 2014-03-30
**gksudo leafpad /var/crash/_usr_bin_Xorg.0.crash** will open it, or mousepad, depending on Lubuntu version.
Does the filename really start with an underscore?

---

### Post by Tar_Ni on 2014-03-31
Thanks ajgreeny,

I was able to open the crash report and I can see it.

I am no computer expert so obviously I can,t make anything out of this bunch of numbers and letters.

What should I look for?

---

### Post by kc1di on 2014-04-01
copy it and post it here.

---

### Post by Tar_Ni on 2014-04-04
```
ProblemType: Crash
Architecture: i386
Date: Sun Mar 30 13:18:17 2014
DistroRelease: Ubuntu 13.10
ExecutablePath: /usr/bin/Xorg
ExecutableTimestamp: 1387274787
ProcCmdline: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
ProcCwd: /etc/X11
ProcEnviron: 
ProcMaps:
 b168a000-b188a000 rw-s 1095de000 00:05 8279      /dev/dri/card0
 b188a000-b2074000 rw-p 00000000 00:00 0 
 b2093000-b21d4000 rw-p 00000000 00:00 0 
 b21d4000-b2314000 rw-s 103476000 00:05 8279      /dev/dri/card0
 b2314000-b2714000 rw-s 00000000 00:04 557060     /SYSV00000000 (deleted)
 b2714000-b2774000 rw-s 00000000 00:04 229379     /SYSV00000000 (deleted)
 b2874000-b4874000 rw-s 00000000 00:04 65536      /SYSV00000000 (deleted)
 b4874000-b487c000 rw-s 101034000 00:05 8279      /dev/dri/card0
 b487c000-b4884000 rw-s 10102c000 00:05 8279      /dev/dri/card0
 b48a4000-b4904000 rw-s 00000000 00:04 196610     /SYSV00000000 (deleted)
 b4904000-b4984000 rw-s 00000000 00:04 163841     /SYSV00000000 (deleted)
 b4984000-b498f000 r-xp 00000000 08:01 918479     /lib/i386-linux-gnu/libnss_files-2.17.so
 b498f000-b4990000 r--p 0000a000 08:01 918479     /lib/i386-linux-gnu/libnss_files-2.17.so
 b4990000-b4991000 rw-p 0000b000 08:01 918479     /lib/i386-linux-gnu/libnss_files-2.17.so
 b4991000-b499b000 r-xp 00000000 08:01 918483     /lib/i386-linux-gnu/libnss_nis-2.17.so
 b499b000-b499c000 r--p 00009000 08:01 918483     /lib/i386-linux-gnu/libnss_nis-2.17.so
 b499c000-b499d000 rw-p 0000a000 08:01 918483     /lib/i386-linux-gnu/libnss_nis-2.17.so
 b499d000-b49b2000 r-xp 00000000 08:01 918473     /lib/i386-linux-gnu/libnsl-2.17.so
 b49b2000-b49b3000 r--p 00014000 08:01 918473     /lib/i386-linux-gnu/libnsl-2.17.so
 b49b3000-b49b4000 rw-p 00015000 08:01 918473     /lib/i386-linux-gnu/libnsl-2.17.so
 b49b4000-b49b6000 rw-p 00000000 00:00 0 
 b49b6000-b49bd000 r-xp 00000000 08:01 918475     /lib/i386-linux-gnu/libnss_compat-2.17.so
 b49bd000-b49be000 r--p 00006000 08:01 918475     /lib/i386-linux-gnu/libnss_compat-2.17.so
 b49be000-b49bf000 rw-p 00007000 08:01 918475     /lib/i386-linux-gnu/libnss_compat-2.17.so
 b49c2000-b49c6000 rw-s 101001000 00:05 8279      /dev/dri/card0
 b49c6000-b49ce000 rw-s 101024000 00:05 8279      /dev/dri/card0
 b49ce000-b4a4e000 rw-s 10186f000 00:05 8279      /dev/dri/card0
 b4a4e000-b605a000 r-xp 00000000 08:01 395832     /usr/lib/i386-linux-gnu/libLLVM-3.3.so.1
 b605a000-b6115000 r--p 0160b000 08:01 395832     /usr/lib/i386-linux-gnu/libLLVM-3.3.so.1
 b6115000-b6117000 rw-p 016c6000 08:01 395832     /usr/lib/i386-linux-gnu/libLLVM-3.3.so.1
 b6117000-b6122000 rw-p 00000000 00:00 0 
 b6122000-b61ff000 r-xp 00000000 08:01 394387     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
 b61ff000-b6203000 r--p 000dc000 08:01 394387     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
 b6203000-b6204000 rw-p 000e0000 08:01 394387     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
 b6204000-b620b000 rw-p 00000000 00:00 0 
 b620b000-b6230000 r-xp 00000000 08:01 918423     /lib/i386-linux-gnu/libexpat.so.1.6.0
 b6230000-b6231000 ---p 00025000 08:01 918423     /lib/i386-linux-gnu/libexpat.so.1.6.0
 b6231000-b6233000 r--p 00025000 08:01 918423     /lib/i386-linux-gnu/libexpat.so.1.6.0
 b6233000-b6234000 rw-p 00027000 08:01 918423     /lib/i386-linux-gnu/libexpat.so.1.6.0
 b6234000-b6468000 r-xp 00000000 08:01 396111     /usr/lib/i386-linux-gnu/libgallium.so.0.0.0
 b6468000-b6472000 r--p 00233000 08:01 396111     /usr/lib/i386-linux-gnu/libgallium.so.0.0.0
 b6472000-b6474000 rw-p 0023d000 08:01 396111     /usr/lib/i386-linux-gnu/libgallium.so.0.0.0
 b6474000-b663c000 rw-p 00000000 00:00 0 
 b663c000-b6a01000 r-xp 00000000 08:01 396041     /usr/lib/i386-linux-gnu/libdricore9.2.1.so.1.0.0
 b6a01000-b6a09000 r--p 003c5000 08:01 396041     /usr/lib/i386-linux-gnu/libdricore9.2.1.so.1.0.0
 b6a09000-b6a0f000 rw-p 003cd000 08:01 396041     /usr/lib/i386-linux-gnu/libdricore9.2.1.so.1.0.0
 b6a0f000-b6a24000 rw-p 00000000 00:00 0 
 b6a24000-b6b6b000 r-xp 00000000 08:01 396867     /usr/lib/i386-linux-gnu/dri/nouveau_dri.so
 b6b6b000-b6b6d000 r--p 00146000 08:01 396867     /usr/lib/i386-linux-gnu/dri/nouveau_dri.so
 b6b6d000-b6b6e000 rw-p 00148000 08:01 396867     /usr/lib/i386-linux-gnu/dri/nouveau_dri.so
 b6b6e000-b6bb1000 rw-p 00000000 00:00 0 
 b6bb1000-b6bd1000 rw-s 10103c000 00:05 8279      /dev/dri/card0
 b6bd1000-b6bd8000 r-xp 00000000 08:01 530294     /usr/lib/xorg/modules/libshadowfb.so
 b6bd8000-b6bd9000 r--p 00006000 08:01 530294     /usr/lib/xorg/modules/libshadowfb.so
 b6bd9000-b6bda000 rw-p 00007000 08:01 530294     /usr/lib/xorg/modules/libshadowfb.so
 b6bda000-b6bf0000 r-xp 00000000 08:01 525669     /usr/lib/xorg/modules/libexa.so
 b6bf0000-b6bf1000 r--p 00015000 08:01 525669     /usr/lib/xorg/modules/libexa.so
 b6bf1000-b6bf2000 rw-p 00016000 08:01 525669     /usr/lib/xorg/modules/libexa.so
 b6bf2000-b6c15000 r-xp 00000000 08:01 530292     /usr/lib/xorg/modules/libfb.so
 b6c15000-b6c16000 r--p 00022000 08:01 530292     /usr/lib/xorg/modules/libfb.so
 b6c16000-b6c17000 rw-p 00023000 08:01 530292     /usr/lib/xorg/modules/libfb.so
 b6c18000-b6c19000 rw-s 1095d9000 00:05 8279      /dev/dri/card0
 b6c19000-b6c1a000 rw-s 00000000 00:04 360453     /SYSV00000000 (deleted)
 b6c1a000-b6c26000 r-xp 00000000 08:01 526673     /usr/lib/xorg/modules/input/evdev_drv.so
 b6c26000-b6c27000 r--p 0000c000 08:01 526673     /usr/lib/xorg/modules/input/evdev_drv.so
 b6c27000-b6c28000 rw-p 0000d000 08:01 526673     /usr/lib/xorg/modules/input/evdev_drv.so
 b6c28000-b6c2e000 r-xp 00000000 08:01 396044     /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
 b6c2e000-b6c2f000 r--p 00005000 08:01 396044     /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
 b6c2f000-b6c30000 rw-p 00006000 08:01 396044     /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
 b6c30000-b6c5f000 r-xp 00000000 08:01 526658     /usr/lib/xorg/modules/drivers/nouveau_drv.so
 b6c5f000-b6c60000 r--p 0002e000 08:01 526658     /usr/lib/xorg/modules/drivers/nouveau_drv.so
 b6c60000-b6c63000 rw-p 0002f000 08:01 526658     /usr/lib/xorg/modules/drivers/nouveau_drv.so
 b6c63000-b6cd5000 r-xp 00000000 08:01 525668     /usr/lib/xorg/modules/extensions/libglx.so
 b6cd5000-b6cd6000 r--p 00071000 08:01 525668     /usr/lib/xorg/modules/extensions/libglx.so
 b6cd6000-b6cd8000 rw-p 00072000 08:01 525668     /usr/lib/xorg/modules/extensions/libglx.so
 b6cd8000-b6cd9000 rw-p 00000000 00:00 0 
 b6cd9000-b6cdd000 r-xp 00000000 08:01 395891     /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
 b6cdd000-b6cde000 r--p 00004000 08:01 395891     /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
 b6cde000-b6cdf000 rw-p 00005000 08:01 395891     /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
 b6cdf000-b6cf5000 r-xp 00000000 08:01 396648     /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
 b6cf5000-b6cf6000 r--p 00016000 08:01 396648     /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
 b6cf6000-b6cf7000 rw-p 00017000 08:01 396648     /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
 b6cf7000-b6cfb000 r-xp 00000000 08:01 395859     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6cfb000-b6cfc000 r--p 00003000 08:01 395859     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6cfc000-b6cfd000 rw-p 00004000 08:01 395859     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6cfd000-b6cff000 r-xp 00000000 08:01 395853     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b6cff000-b6d00000 r--p 00001000 08:01 395853     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b6d00000-b6d01000 rw-p 00002000 08:01 395853     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b6d01000-b6d12000 r-xp 00000000 08:01 395857     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b6d12000-b6d13000 r--p 00010000 08:01 395857     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b6d13000-b6d14000 rw-p 00011000 08:01 395857     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b6d14000-b6d19000 r-xp 00000000 08:01 396083     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6d19000-b6d1a000 r--p 00005000 08:01 396083     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6d1a000-b6d1b000 rw-p 00006000 08:01 396083     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6d1b000-b6d6d000 r-xp 00000000 08:01 397489     /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
 b6d6d000-b6d6f000 r--p 00051000 08:01 397489     /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
 b6d6f000-b6d74000 rwxp 00053000 08:01 397489     /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
 b6d74000-b6d81000 r-xp 00000000 08:01 396631     /usr/lib/i386-linux-gnu/libwayland-server.so.0.0.0
 b6d81000-b6d82000 ---p 0000d000 08:01 396631     /usr/lib/i386-linux-gnu/libwayland-server.so.0.0.0
 b6d82000-b6d83000 r--p 0000d000 08:01 396631     /usr/lib/i386-linux-gnu/libwayland-server.so.0.0.0
 b6d83000-b6d84000 rw-p 0000e000 08:01 396631     /usr/lib/i386-linux-gnu/libwayland-server.so.0.0.0
 b6d84000-b6d8c000 r-xp 00000000 08:01 396627     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b6d8c000-b6d8d000 r--p 00008000 08:01 396627     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b6d8d000-b6d8e000 rw-p 00009000 08:01 396627     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b6d8e000-b6dad000 r-xp 00000000 08:01 396660     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b6dad000-b6dae000 r--p 0001f000 08:01 396660     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b6dae000-b6daf000 rw-p 00020000 08:01 396660     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b6daf000-b6db5000 r-xp 00000000 08:01 396658     /usr/lib/i386-linux-gnu/libxcb-xfixes.so.0.0.0
 b6db5000-b6db6000 r--p 00005000 08:01 396658     /usr/lib/i386-linux-gnu/libxcb-xfixes.so.0.0.0
 b6db6000-b6db7000 rw-p 00006000 08:01 396658     /usr/lib/i386-linux-gnu/libxcb-xfixes.so.0.0.0
 b6db7000-b6dbb000 r-xp 00000000 08:01 396646     /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
 b6dbb000-b6dbc000 r--p 00003000 08:01 396646     /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
 b6dbc000-b6dbd000 rw-p 00004000 08:01 396646     /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
 b6dbd000-b6eed000 r-xp 00000000 08:01 395840     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b6eed000-b6eee000 ---p 00130000 08:01 395840     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b6eee000-b6eef000 r--p 00130000 08:01 395840     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b6eef000-b6ef1000 rw-p 00131000 08:01 395840     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b6ef1000-b6ef2000 rw-p 00000000 00:00 0 
 b6ef2000-b6ef3000 r-xp 00000000 08:01 395838     /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 b6ef3000-b6ef4000 r--p 00000000 08:01 395838     /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 b6ef4000-b6ef5000 rw-p 00001000 08:01 395838     /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 b6ef5000-b6f28000 r-xp 00000000 08:01 396102     /usr/lib/i386-linux-gnu/libglamor.so.0.0.0
 b6f28000-b6f29000 r--p 00032000 08:01 396102     /usr/lib/i386-linux-gnu/libglamor.so.0.0.0
 b6f29000-b6f2a000 rw-p 00033000 08:01 396102     /usr/lib/i386-linux-gnu/libglamor.so.0.0.0
 b6f2a000-b6f32000 rw-p 00000000 00:00 0 
 b6f32000-b6f41000 r-xp 00000000 08:01 396160     /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 b6f41000-b6f43000 r--p 0000f000 08:01 396160     /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 b6f43000-b6f48000 rwxp 00011000 08:01 396160     /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 b6f48000-b6f69000 r-xp 00000000 08:01 397492     /usr/lib/i386-linux-gnu/mesa-egl/libEGL.so.1.0.0
 b6f69000-b6f6a000 r--p 00020000 08:01 397492     /usr/lib/i386-linux-gnu/mesa-egl/libEGL.so.1.0.0
 b6f6a000-b6f6b000 rw-p 00021000 08:01 397492     /usr/lib/i386-linux-gnu/mesa-egl/libEGL.so.1.0.0
 b6f6b000-b6f70000 r-xp 00000000 08:01 396399     /usr/lib/i386-linux-gnu/libmtdev.so.1.0.0
 b6f70000-b6f71000 r--p 00004000 08:01 396399     /usr/lib/i386-linux-gnu/libmtdev.so.1.0.0
 b6f71000-b6f72000 rw-p 00005000 08:01 396399     /usr/lib/i386-linux-gnu/libmtdev.so.1.0.0
 b6f72000-b6f7a000 rw-s 10101c000 00:05 8279      /dev/dri/card0
 b6f7a000-b6fbb000 rw-p 00000000 00:00 0 
 b6fbb000-b6fd6000 r-xp 00000000 08:01 917508     /lib/i386-linux-gnu/libgcc_s.so.1
 b6fd6000-b6fd7000 r--p 0001a000 08:01 917508     /lib/i386-linux-gnu/libgcc_s.so.1
 b6fd7000-b6fd8000 rw-p 0001b000 08:01 917508     /lib/i386-linux-gnu/libgcc_s.so.1
 b6fd8000-b6fdb000 rw-p 00000000 00:00 0 
 b6fdb000-b6fe0000 r-xp 00000000 08:01 396095     /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b6fe0000-b6fe1000 r--p 00004000 08:01 396095     /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b6fe1000-b6fe2000 rw-p 00005000 08:01 396095     /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b6fe2000-b6ff1000 r-xp 00000000 08:01 918402     /lib/i386-linux-gnu/libbz2.so.1.0.4
 b6ff1000-b6ff2000 r--p 0000e000 08:01 918402     /lib/i386-linux-gnu/libbz2.so.1.0.4
 b6ff2000-b6ff3000 rw-p 0000f000 08:01 918402     /lib/i386-linux-gnu/libbz2.so.1.0.4
 b6ff3000-b708d000 r-xp 00000000 08:01 396048     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
 b708d000-b7091000 r--p 00099000 08:01 396048     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
 b7091000-b7092000 rw-p 0009d000 08:01 396048     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
 b7092000-b70aa000 r-xp 00000000 08:01 918558     /lib/i386-linux-gnu/libz.so.1.2.8
 b70aa000-b70ab000 r--p 00017000 08:01 918558     /lib/i386-linux-gnu/libz.so.1.2.8
 b70ab000-b70ac000 rw-p 00018000 08:01 918558     /lib/i386-linux-gnu/libz.so.1.2.8
 b70ac000-b70ad000 rw-p 00000000 00:00 0 
 b70ad000-b70b0000 r-xp 00000000 08:01 918434     /lib/i386-linux-gnu/libgpg-error.so.0.10.0
 b70b0000-b70b1000 r--p 00002000 08:01 918434     /lib/i386-linux-gnu/libgpg-error.so.0.10.0
 b70b1000-b70b2000 rw-p 00003000 08:01 918434     /lib/i386-linux-gnu/libgpg-error.so.0.10.0
 b70b2000-b70f1000 r-xp 00000000 08:01 918501     /lib/i386-linux-gnu/libpcre.so.3.13.1
 b70f1000-b70f2000 r--p 0003f000 08:01 918501     /lib/i386-linux-gnu/libpcre.so.3.13.1
 b70f2000-b70f3000 rw-p 00040000 08:01 918501     /lib/i386-linux-gnu/libpcre.so.3.13.1
 b70f3000-b70fa000 r-xp 00000000 08:01 918526     /lib/i386-linux-gnu/librt-2.17.so
 b70fa000-b70fb000 r--p 00006000 08:01 918526     /lib/i386-linux-gnu/librt-2.17.so
 b70fb000-b70fc000 rw-p 00007000 08:01 918526     /lib/i386-linux-gnu/librt-2.17.so
 b70fc000-b72aa000 r-xp 00000000 08:01 918403     /lib/i386-linux-gnu/libc-2.17.so
 b72aa000-b72ac000 r--p 001ae000 08:01 918403     /lib/i386-linux-gnu/libc-2.17.so
 b72ac000-b72ad000 rw-p 001b0000 08:01 918403     /lib/i386-linux-gnu/libc-2.17.so
 b72ad000-b72b0000 rw-p 00000000 00:00 0 
 b72b0000-b72f1000 r-xp 00000000 08:01 918454     /lib/i386-linux-gnu/libm-2.17.so
 b72f1000-b72f2000 r--p 00040000 08:01 918454     /lib/i386-linux-gnu/libm-2.17.so
 b72f2000-b72f3000 rw-p 00041000 08:01 918454     /lib/i386-linux-gnu/libm-2.17.so
 b72f3000-b72f4000 rw-p 00000000 00:00 0 
 b72f4000-b730d000 r-xp 00000000 08:01 918395     /lib/i386-linux-gnu/libaudit.so.1.0.0
 b730d000-b730e000 r--p 00018000 08:01 918395     /lib/i386-linux-gnu/libaudit.so.1.0.0
 b730e000-b730f000 rw-p 00019000 08:01 918395     /lib/i386-linux-gnu/libaudit.so.1.0.0
 b730f000-b7313000 rw-p 00000000 00:00 0 
 b7313000-b7318000 r-xp 00000000 08:01 395855     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b7318000-b7319000 r--p 00004000 08:01 395855     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b7319000-b731a000 rw-p 00005000 08:01 395855     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b731a000-b731c000 r-xp 00000000 08:01 395844     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b731c000-b731d000 r--p 00001000 08:01 395844     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b731d000-b731e000 rw-p 00002000 08:01 395844     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b731e000-b7357000 r-xp 00000000 08:01 396600     /usr/lib/i386-linux-gnu/libXfont.so.1.4.1
 b7357000-b7358000 r--p 00038000 08:01 396600     /usr/lib/i386-linux-gnu/libXfont.so.1.4.1
 b7358000-b7359000 rw-p 00039000 08:01 396600     /usr/lib/i386-linux-gnu/libXfont.so.1.4.1
 b7359000-b735a000 rw-p 00000000 00:00 0 
 b735a000-b73fe000 r-xp 00000000 08:01 396547     /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
 b73fe000-b7403000 r--p 000a4000 08:01 396547     /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
 b7403000-b7404000 rw-p 000a9000 08:01 396547     /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
 b7404000-b7405000 rw-p 00000000 00:00 0 
 b7405000-b7410000 r-xp 00000000 08:01 397501     /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7410000-b7411000 r--p 0000a000 08:01 397501     /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7411000-b7412000 rw-p 0000b000 08:01 397501     /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7412000-b7429000 r-xp 00000000 08:01 918518     /lib/i386-linux-gnu/libpthread-2.17.so
 b7429000-b742a000 r--p 00016000 08:01 918518     /lib/i386-linux-gnu/libpthread-2.17.so
 b742a000-b742b000 rw-p 00017000 08:01 918518     /lib/i386-linux-gnu/libpthread-2.17.so
 b742b000-b742d000 rw-p 00000000 00:00 0 
 b742d000-b7436000 r-xp 00000000 08:01 396462     /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b7436000-b7437000 r--p 00008000 08:01 396462     /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b7437000-b7438000 rw-p 00009000 08:01 396462     /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b7438000-b743b000 r-xp 00000000 08:01 918418     /lib/i386-linux-gnu/libdl-2.17.so
 b743b000-b743c000 r--p 00002000 08:01 918418     /lib/i386-linux-gnu/libdl-2.17.so
 b743c000-b743d000 rw-p 00003000 08:01 918418     /lib/i386-linux-gnu/libdl-2.17.so
 b743d000-b74be000 r-xp 00000000 08:01 918430     /lib/i386-linux-gnu/libgcrypt.so.11.7.0
 b74be000-b74bf000 r--p 00081000 08:01 918430     /lib/i386-linux-gnu/libgcrypt.so.11.7.0
 b74bf000-b74c1000 rw-p 00082000 08:01 918430     /lib/i386-linux-gnu/libgcrypt.so.11.7.0
 b74c1000-b74c2000 rw-p 00000000 00:00 0 
 b74c2000-b74e2000 r-xp 00000000 08:01 918528     /lib/i386-linux-gnu/libselinux.so.1
 b74e2000-b74e3000 r--p 0001f000 08:01 918528     /lib/i386-linux-gnu/libselinux.so.1
 b74e3000-b74e4000 rw-p 00020000 08:01 918528     /lib/i386-linux-gnu/libselinux.so.1
 b74e4000-b74f5000 r-xp 00000000 08:01 917559     /lib/i386-linux-gnu/libudev.so.1.3.5
 b74f5000-b74f6000 r--p 00010000 08:01 917559     /lib/i386-linux-gnu/libudev.so.1.3.5
 b74f6000-b74f7000 rw-p 00011000 08:01 917559     /lib/i386-linux-gnu/libudev.so.1.3.5
 b74f7000-b74f8000 rw-s 101a6f000 00:05 8279      /dev/dri/card0
 b74f8000-b74fe000 r-xp 00000000 08:01 396113     /usr/lib/i386-linux-gnu/libgbm.so.1.0.0
 b74fe000-b74ff000 r--p 00005000 08:01 396113     /usr/lib/i386-linux-gnu/libgbm.so.1.0.0
 b74ff000-b7500000 rw-p 00006000 08:01 396113     /usr/lib/i386-linux-gnu/libgbm.so.1.0.0
 b7500000-b7503000 r-xp 00000000 08:01 526642     /usr/lib/xorg/modules/libglamoregl.so
 b7503000-b7504000 r--p 00002000 08:01 526642     /usr/lib/xorg/modules/libglamoregl.so
 b7504000-b7505000 rw-p 00003000 08:01 526642     /usr/lib/xorg/modules/libglamoregl.so
 b7505000-b7508000 rw-p 00000000 00:00 0 
 b7508000-b7509000 r-xp 00000000 00:00 0          [vdso]
 b7509000-b7529000 r-xp 00000000 08:01 918379     /lib/i386-linux-gnu/ld-2.17.so
 b7529000-b752a000 r--p 0001f000 08:01 918379     /lib/i386-linux-gnu/ld-2.17.so
 b752a000-b752b000 rw-p 00020000 08:01 918379     /lib/i386-linux-gnu/ld-2.17.so
 b752b000-b774e000 r-xp 00000000 08:01 394196     /usr/bin/Xorg
 b774e000-b774f000 r--p 00223000 08:01 394196     /usr/bin/Xorg
 b774f000-b7756000 rw-p 00224000 08:01 394196     /usr/bin/Xorg
 b7756000-b7763000 rw-p 00000000 00:00 0 
 b7c85000-b82c6000 rw-p 00000000 00:00 0          [heap]
 bffb4000-bffd8000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:    Xorg
 State:    S (sleeping)
 Tgid:    1013
 Pid:    1013
 PPid:    956
 TracerPid:    0
 Uid:    0    0    0    0
 Gid:    0    0    0    0
 FDSize:    256
 Groups:    0 
 VmPeak:      116752 kB
 VmSize:      104432 kB
 VmLck:           0 kB
 VmPin:           0 kB
 VmHWM:       38916 kB
 VmRSS:       33292 kB
 VmData:       18484 kB
 VmStk:         148 kB
 VmExe:        2188 kB
 VmLib:       39872 kB
 VmPTE:         156 kB
 VmSwap:           0 kB
 Threads:    1
 SigQ:    0/7878
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    000000001a392400
 SigIgn:    0000000000001000
 SigCgt:    00000001d18066cf
 CapInh:    0000000000000000
 CapPrm:    0000001fffffffff
 CapEff:    0000001fffffffff
 CapBnd:    0000001fffffffff
 Seccomp:    0
 Cpus_allowed:    3
 Cpus_allowed_list:    0-1
 Mems_allowed:    1
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    204154
 nonvoluntary_ctxt_switches:    34528
Signal: 6
Uname: Linux 3.11.0-18-generic i686
UserGroups: 
CoreDump: base64
```

---

