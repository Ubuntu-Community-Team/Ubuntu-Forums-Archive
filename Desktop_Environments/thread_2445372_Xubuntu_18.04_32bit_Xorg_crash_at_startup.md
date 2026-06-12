---
title: "Xubuntu 18.04 32bit Xorg crash at startup"
date: 2020-06-13
forum: Desktop Environments
---

### Post by libertyspike138 on 2020-06-13
Hello, I recently did a fresh install of Xubuntu Core 18.04 32 bit on my old P4 machine. For the most part everything seems to be working OK and I now have all the apps I want installed. I did have a Geforce 6200 in it but it was giving me some issues so I swapped it for a Radeon 9250. My problem is right after I log in I get notified of a system problem and when I check /var/crash I see it is xorg crashing because of something to do with lightdm. This error does not happen all of the time but most of the time. I have been playing around with it a good bit to try and figure it out. I also switched display managers to see if the error would go away and it did but GDM takes too long to load, XDM & WDM are not loading my xprofile, using systemd, etc. so I want to use lightdm but without errors. I also checked to see if I could upgrade to a newer version of lightdm but 1.30 has some dependencies that are not available until version 19.04 and it is 64 bit only. I have attached my crash log minus the dump so I'm hoping that somebody can point me in the right direction with this. Thanks!

```
ProblemType: Crash
Architecture: i386
Date: Sat Jun 13 02:54:39 2020
DistroRelease: Ubuntu 18.04
ExecutablePath: /usr/lib/xorg/Xorg
ExecutableTimestamp: 1571667977
ProcCmdline: /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
ProcCwd: /
ProcEnviron: PATH=(custom, no user)
ProcMaps:
 00471000-006e6000 r-xp 00000000 08:03 3279515    /usr/lib/xorg/Xorg
 006e7000-006e9000 r--p 00275000 08:03 3279515    /usr/lib/xorg/Xorg
 006e9000-006ef000 rw-p 00277000 08:03 3279515    /usr/lib/xorg/Xorg
 006ef000-00707000 rw-p 00000000 00:00 0 
 00733000-00bce000 rw-p 00000000 00:00 0          [heap]
 aebc4000-aff75000 rw-p 00000000 00:00 0 
 aff75000-aff7b000 r-xp 00000000 08:03 1977091    /usr/lib/i386-linux-gnu/libxcb-sync.so.1.0.0
 aff7b000-aff7c000 r--p 00005000 08:03 1977091    /usr/lib/i386-linux-gnu/libxcb-sync.so.1.0.0
 aff7c000-aff7d000 rw-p 00006000 08:03 1977091    /usr/lib/i386-linux-gnu/libxcb-sync.so.1.0.0
 aff7d000-aff7f000 r-xp 00000000 08:03 1977089    /usr/lib/i386-linux-gnu/libxcb-present.so.0.0.0
 aff7f000-aff80000 r--p 00001000 08:03 1977089    /usr/lib/i386-linux-gnu/libxcb-present.so.0.0.0
 aff80000-aff81000 rw-p 00002000 08:03 1977089    /usr/lib/i386-linux-gnu/libxcb-present.so.0.0.0
 aff81000-aff84000 r-xp 00000000 08:03 1977087    /usr/lib/i386-linux-gnu/libxcb-dri3.so.0.0.0
 aff84000-aff85000 r--p 00002000 08:03 1977087    /usr/lib/i386-linux-gnu/libxcb-dri3.so.0.0.0
 aff85000-aff86000 rw-p 00003000 08:03 1977087    /usr/lib/i386-linux-gnu/libxcb-dri3.so.0.0.0
 aff86000-aff91000 r-xp 00000000 08:03 1973553    /usr/lib/i386-linux-gnu/libwayland-client.so.0.3.0
 aff91000-aff92000 ---p 0000b000 08:03 1973553    /usr/lib/i386-linux-gnu/libwayland-client.so.0.3.0
 aff92000-aff93000 r--p 0000b000 08:03 1973553    /usr/lib/i386-linux-gnu/libwayland-client.so.0.3.0
 aff93000-aff94000 rw-p 0000c000 08:03 1973553    /usr/lib/i386-linux-gnu/libwayland-client.so.0.3.0
 aff94000-aff9b000 r-xp 00000000 08:03 1977093    /usr/lib/i386-linux-gnu/libxcb-xfixes.so.0.0.0
 aff9b000-aff9c000 r--p 00006000 08:03 1977093    /usr/lib/i386-linux-gnu/libxcb-xfixes.so.0.0.0
 aff9c000-aff9d000 rw-p 00007000 08:03 1977093    /usr/lib/i386-linux-gnu/libxcb-xfixes.so.0.0.0
 aff9d000-affa1000 r-xp 00000000 08:03 1977085    /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
 affa1000-affa2000 r--p 00003000 08:03 1977085    /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
 affa2000-affa3000 rw-p 00004000 08:03 1977085    /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
 affa3000-affe6000 r-xp 00000000 08:03 1977097    /usr/lib/i386-linux-gnu/libEGL_mesa.so.0.0.0
 affe6000-affe8000 r--p 00042000 08:03 1977097    /usr/lib/i386-linux-gnu/libEGL_mesa.so.0.0.0
 affe8000-affe9000 rw-p 00044000 08:03 1977097    /usr/lib/i386-linux-gnu/libEGL_mesa.so.0.0.0
 affe9000-afffc000 r-xp 00000000 08:03 1977099    /usr/lib/i386-linux-gnu/libEGL.so.1.0.0
 afffc000-afffd000 r--p 00012000 08:03 1977099    /usr/lib/i386-linux-gnu/libEGL.so.1.0.0
 afffd000-afffe000 rw-p 00013000 08:03 1977099    /usr/lib/i386-linux-gnu/libEGL.so.1.0.0
 afffe000-b0023000 r-xp 00000000 08:03 1977105    /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 b0023000-b0024000 r--p 00024000 08:03 1977105    /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 b0024000-b0025000 rw-p 00025000 08:03 1977105    /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 b0025000-b0c15000 r-xp 00000000 08:03 2233018    /usr/lib/i386-linux-gnu/dri/r200_dri.so
 b0c15000-b0c8c000 r--p 00bef000 08:03 2233018    /usr/lib/i386-linux-gnu/dri/r200_dri.so
 b0c8c000-b0ccf000 rw-p 00c66000 08:03 2233018    /usr/lib/i386-linux-gnu/dri/r200_dri.so
 b0ccf000-b0d7d000 rw-p 00000000 00:00 0 
 b0d7d000-b0d8d000 r-xp 00000000 08:03 1977077    /usr/lib/i386-linux-gnu/libwayland-server.so.0.1.0
 b0d8d000-b0d8e000 r--p 0000f000 08:03 1977077    /usr/lib/i386-linux-gnu/libwayland-server.so.0.1.0
 b0d8e000-b0d8f000 rw-p 00010000 08:03 1977077    /usr/lib/i386-linux-gnu/libwayland-server.so.0.1.0
 b0d8f000-b0e77000 r-xp 00000000 08:03 1973529    /usr/lib/i386-linux-gnu/libepoxy.so.0.0.0
 b0e77000-b0e7b000 r--p 000e7000 08:03 1973529    /usr/lib/i386-linux-gnu/libepoxy.so.0.0.0
 b0e7b000-b0e7f000 rw-p 000eb000 08:03 1973529    /usr/lib/i386-linux-gnu/libepoxy.so.0.0.0
 b0e7f000-b0e8d000 r-xp 00000000 08:03 1977079    /usr/lib/i386-linux-gnu/libgbm.so.1.0.0
 b0e8d000-b0e8e000 ---p 0000e000 08:03 1977079    /usr/lib/i386-linux-gnu/libgbm.so.1.0.0
 b0e8e000-b0e8f000 r--p 0000e000 08:03 1977079    /usr/lib/i386-linux-gnu/libgbm.so.1.0.0
 b0e8f000-b0e90000 rw-p 0000f000 08:03 1977079    /usr/lib/i386-linux-gnu/libgbm.so.1.0.0
 b0e90000-b0ec3000 r-xp 00000000 08:03 3419444    /usr/lib/xorg/modules/libglamoregl.so
 b0ec3000-b0ec4000 ---p 00033000 08:03 3419444    /usr/lib/xorg/modules/libglamoregl.so
 b0ec4000-b0ec5000 r--p 00033000 08:03 3419444    /usr/lib/xorg/modules/libglamoregl.so
 b0ec5000-b0ec6000 rw-p 00034000 08:03 3419444    /usr/lib/xorg/modules/libglamoregl.so
 b0ec6000-b0ff4000 r-xp 00000000 08:03 1969134    /usr/lib/i386-linux-gnu/libglib-2.0.so.0.5600.4
 b0ff4000-b0ff5000 ---p 0012e000 08:03 1969134    /usr/lib/i386-linux-gnu/libglib-2.0.so.0.5600.4
 b0ff5000-b0ff6000 r--p 0012e000 08:03 1969134    /usr/lib/i386-linux-gnu/libglib-2.0.so.0.5600.4
 b0ff6000-b0ff7000 rw-p 0012f000 08:03 1969134    /usr/lib/i386-linux-gnu/libglib-2.0.so.0.5600.4
 b0ff7000-b1054000 r-xp 00000000 08:03 1969136    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.5600.4
 b1054000-b1055000 ---p 0005d000 08:03 1969136    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.5600.4
 b1055000-b1056000 r--p 0005d000 08:03 1969136    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.5600.4
 b1056000-b1057000 rw-p 0005e000 08:03 1969136    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.5600.4
 b1057000-b1061000 r-xp 00000000 08:03 1976594    /usr/lib/i386-linux-gnu/libgudev-1.0.so.0.2.0
 b1061000-b1062000 r--p 00009000 08:03 1976594    /usr/lib/i386-linux-gnu/libgudev-1.0.so.0.2.0
 b1062000-b1063000 rw-p 0000a000 08:03 1976594    /usr/lib/i386-linux-gnu/libgudev-1.0.so.0.2.0
 b1063000-b106d000 r-xp 00000000 08:03 1978033    /usr/lib/i386-linux-gnu/libwacom.so.2.6.1
 b106d000-b106e000 r--p 00009000 08:03 1978033    /usr/lib/i386-linux-gnu/libwacom.so.2.6.1
 b106e000-b106f000 rw-p 0000a000 08:03 1978033    /usr/lib/i386-linux-gnu/libwacom.so.2.6.1
 b106f000-b107e000 r-xp 00000000 08:03 1978035    /usr/lib/i386-linux-gnu/libevdev.so.2.1.20
 b107e000-b107f000 ---p 0000f000 08:03 1978035    /usr/lib/i386-linux-gnu/libevdev.so.2.1.20
 b107f000-b1082000 r--p 0000f000 08:03 1978035    /usr/lib/i386-linux-gnu/libevdev.so.2.1.20
 b1082000-b1083000 rw-p 00012000 08:03 1978035    /usr/lib/i386-linux-gnu/libevdev.so.2.1.20
 b1083000-b10c3000 r-xp 00000000 08:03 1978042    /usr/lib/i386-linux-gnu/libinput.so.10.13.0
 b10c3000-b10c4000 r--p 0003f000 08:03 1978042    /usr/lib/i386-linux-gnu/libinput.so.10.13.0
 b10c4000-b10c5000 rw-p 00040000 08:03 1978042    /usr/lib/i386-linux-gnu/libinput.so.10.13.0
 b10df000-b10ff000 r-xp 00000000 08:03 5111879    /lib/i386-linux-gnu/libtinfo.so.5.9
 b10ff000-b1101000 r--p 0001f000 08:03 5111879    /lib/i386-linux-gnu/libtinfo.so.5.9
 b1101000-b1102000 rw-p 00021000 08:03 5111879    /lib/i386-linux-gnu/libtinfo.so.5.9
 b1102000-b1134000 r-xp 00000000 08:03 1975585    /usr/lib/i386-linux-gnu/libedit.so.2.0.56
 b1134000-b1135000 ---p 00032000 08:03 1975585    /usr/lib/i386-linux-gnu/libedit.so.2.0.56
 b1135000-b1136000 r--p 00032000 08:03 1975585    /usr/lib/i386-linux-gnu/libedit.so.2.0.56
 b1136000-b1137000 rw-p 00033000 08:03 1975585    /usr/lib/i386-linux-gnu/libedit.so.2.0.56
 b1137000-b1139000 rw-p 00000000 00:00 0 
 b1139000-b1140000 r-xp 00000000 08:03 1970913    /usr/lib/i386-linux-gnu/libffi.so.6.0.4
 b1140000-b1141000 r--p 00006000 08:03 1970913    /usr/lib/i386-linux-gnu/libffi.so.6.0.4
 b1141000-b1142000 rw-p 00007000 08:03 1970913    /usr/lib/i386-linux-gnu/libffi.so.6.0.4
 b1142000-b1148000 r-xp 00000000 08:03 1977112    /usr/lib/i386-linux-gnu/libatomic.so.1.2.0
 b1148000-b1149000 r--p 00005000 08:03 1977112    /usr/lib/i386-linux-gnu/libatomic.so.1.2.0
 b1149000-b114a000 rw-p 00006000 08:03 1977112    /usr/lib/i386-linux-gnu/libatomic.so.1.2.0
 b114a000-b114b000 rw-p 00000000 00:00 0 
 b114b000-b12c7000 r-xp 00000000 08:03 1966693    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.25
 b12c7000-b12cd000 r--p 0017b000 08:03 1966693    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.25
 b12cd000-b12ce000 rw-p 00181000 08:03 1966693    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.25
 b12ce000-b12d1000 rw-p 00000000 00:00 0 
 b12d1000-b12d9000 r-xp 00000000 08:03 1977107    /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
 b12d9000-b12da000 r--p 00007000 08:03 1977107    /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
 b12da000-b12db000 rw-p 00008000 08:03 1977107    /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
 b12db000-b12e5000 r-xp 00000000 08:03 1977103    /usr/lib/i386-linux-gnu/libdrm_amdgpu.so.1.0.0
 b12e5000-b12e6000 r--p 00009000 08:03 1977103    /usr/lib/i386-linux-gnu/libdrm_amdgpu.so.1.0.0
 b12e6000-b12e7000 rw-p 0000a000 08:03 1977103    /usr/lib/i386-linux-gnu/libdrm_amdgpu.so.1.0.0
 b12e7000-b1303000 r-xp 00000000 08:03 1967788    /usr/lib/i386-linux-gnu/libelf-0.170.so
 b1303000-b1304000 r--p 0001b000 08:03 1967788    /usr/lib/i386-linux-gnu/libelf-0.170.so
 b1304000-b1305000 rw-p 0001c000 08:03 1967788    /usr/lib/i386-linux-gnu/libelf-0.170.so
 b1305000-b1313000 r-xp 00000000 08:03 1977122    /usr/lib/i386-linux-gnu/libsensors.so.4.4.0
 b1313000-b1314000 r--p 0000d000 08:03 1977122    /usr/lib/i386-linux-gnu/libsensors.so.4.4.0
 b1314000-b1315000 rw-p 0000e000 08:03 1977122    /usr/lib/i386-linux-gnu/libsensors.so.4.4.0
 b1315000-b1344000 r-xp 00000000 08:03 5111891    /lib/i386-linux-gnu/libexpat.so.1.6.7
 b1344000-b1346000 r--p 0002e000 08:03 5111891    /lib/i386-linux-gnu/libexpat.so.1.6.7
 b1346000-b1347000 rw-p 00030000 08:03 5111891    /lib/i386-linux-gnu/libexpat.so.1.6.7
 b1347000-b4d4f000 r-xp 00000000 08:03 1977115    /usr/lib/i386-linux-gnu/libLLVM-9.so.1
 b4d4f000-b50ab000 r--p 03a07000 08:03 1977115    /usr/lib/i386-linux-gnu/libLLVM-9.so.1
 b50ab000-b50c5000 rw-p 03d63000 08:03 1977115    /usr/lib/i386-linux-gnu/libLLVM-9.so.1
 b50c5000-b5101000 rw-p 00000000 00:00 0 
 b5101000-b5117000 r-xp 00000000 08:03 1977082    /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 b5117000-b5118000 ---p 00016000 08:03 1977082    /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 b5118000-b511a000 r--p 00016000 08:03 1977082    /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 b511a000-b5121000 rwxp 00018000 08:03 1977082    /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 b5124000-b5125000 r-xp 00000000 08:03 1974350    /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 b5125000-b5126000 r--p 00000000 08:03 1974350    /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 b5126000-b5127000 rw-p 00001000 08:03 1974350    /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 b5127000-b5139000 r-xp 00000000 08:03 3807741    /usr/lib/xorg/modules/input/libinput_drv.so
 b5139000-b513a000 r--p 00011000 08:03 3807741    /usr/lib/xorg/modules/input/libinput_drv.so
 b513a000-b513b000 rw-p 00012000 08:03 3807741    /usr/lib/xorg/modules/input/libinput_drv.so
 b513b000-b6491000 r-xp 00000000 08:03 2233019    /usr/lib/i386-linux-gnu/dri/swrast_dri.so
 b6491000-b651a000 r--p 01355000 08:03 2233019    /usr/lib/i386-linux-gnu/dri/swrast_dri.so
 b651a000-b6561000 rw-p 013de000 08:03 2233019    /usr/lib/i386-linux-gnu/dri/swrast_dri.so
 b6561000-b719f000 rw-p 00000000 00:00 0 
 b719f000-b72cf000 rw-s 00000000 00:06 86         /dev/fb0 (deleted)
 b72cf000-b72d6000 r-xp 00000000 08:03 3419717    /usr/lib/xorg/modules/libshadow.so
 b72d6000-b72d7000 ---p 00007000 08:03 3419717    /usr/lib/xorg/modules/libshadow.so
 b72d7000-b72d8000 r--p 00007000 08:03 3419717    /usr/lib/xorg/modules/libshadow.so
 b72d8000-b72d9000 rw-p 00008000 08:03 3419717    /usr/lib/xorg/modules/libshadow.so
 b72d9000-b72fa000 r-xp 00000000 08:03 3419713    /usr/lib/xorg/modules/libfb.so
 b72fa000-b72fb000 r--p 00020000 08:03 3419713    /usr/lib/xorg/modules/libfb.so
 b72fb000-b72fc000 rw-p 00021000 08:03 3419713    /usr/lib/xorg/modules/libfb.so
 b72fc000-b7300000 r-xp 00000000 08:03 3419714    /usr/lib/xorg/modules/libfbdevhw.so
 b7300000-b7301000 r--p 00003000 08:03 3419714    /usr/lib/xorg/modules/libfbdevhw.so
 b7301000-b7302000 rw-p 00004000 08:03 3419714    /usr/lib/xorg/modules/libfbdevhw.so
 b7302000-b7303000 rw-p 00000000 00:00 0 
 b7303000-b7308000 r-xp 00000000 08:03 1978037    /usr/lib/i386-linux-gnu/libmtdev.so.1.0.0
 b7308000-b7309000 r--p 00004000 08:03 1978037    /usr/lib/i386-linux-gnu/libmtdev.so.1.0.0
 b7309000-b730a000 rw-p 00005000 08:03 1978037    /usr/lib/i386-linux-gnu/libmtdev.so.1.0.0
 b730a000-b731f000 r-xp 00000000 08:03 3546456    /usr/lib/xorg/modules/drivers/modesetting_drv.so
 b731f000-b7320000 ---p 00015000 08:03 3546456    /usr/lib/xorg/modules/drivers/modesetting_drv.so
 b7320000-b7321000 r--p 00015000 08:03 3546456    /usr/lib/xorg/modules/drivers/modesetting_drv.so
 b7321000-b7322000 rw-p 00016000 08:03 3546456    /usr/lib/xorg/modules/drivers/modesetting_drv.so
 b7322000-b7397000 r-xp 00000000 08:03 3546458    /usr/lib/xorg/modules/drivers/radeon_drv.so
 b7397000-b7398000 r--p 00074000 08:03 3546458    /usr/lib/xorg/modules/drivers/radeon_drv.so
 b7398000-b739d000 rw-p 00075000 08:03 3546458    /usr/lib/xorg/modules/drivers/radeon_drv.so
 b739d000-b73c7000 r-xp 00000000 08:03 1972923    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b73c7000-b73c8000 r--p 00029000 08:03 1972923    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b73c8000-b73c9000 rw-p 0002a000 08:03 1972923    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b73c9000-b750f000 r-xp 00000000 08:03 1972933    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b750f000-b7510000 r--p 00145000 08:03 1972933    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b7510000-b7512000 rw-p 00146000 08:03 1972933    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b7512000-b7513000 rw-p 00000000 00:00 0 
 b7513000-b754c000 r-xp 00000000 08:03 1977074    /usr/lib/i386-linux-gnu/libGLdispatch.so.0.0.0
 b754c000-b754d000 ---p 00039000 08:03 1977074    /usr/lib/i386-linux-gnu/libGLdispatch.so.0.0.0
 b754d000-b7561000 r--p 00039000 08:03 1977074    /usr/lib/i386-linux-gnu/libGLdispatch.so.0.0.0
 b7561000-b7562000 rw-p 0004d000 08:03 1977074    /usr/lib/i386-linux-gnu/libGLdispatch.so.0.0.0
 b7562000-b7572000 rw-p 00000000 00:00 0 
 b7572000-b7582000 r-xp 00000000 08:03 1977127    /usr/lib/i386-linux-gnu/libGLX.so.0.0.0
 b7582000-b7583000 ---p 00010000 08:03 1977127    /usr/lib/i386-linux-gnu/libGLX.so.0.0.0
 b7583000-b7584000 r--p 00010000 08:03 1977127    /usr/lib/i386-linux-gnu/libGLX.so.0.0.0
 b7584000-b7585000 rw-p 00011000 08:03 1977127    /usr/lib/i386-linux-gnu/libGLX.so.0.0.0
 b7585000-b7595000 rw-p 00000000 00:00 0 
 b7595000-b75e8000 r-xp 00000000 08:03 1971221    /usr/lib/i386-linux-gnu/libGL.so.1.0.0
 b75e8000-b75f5000 r--p 00052000 08:03 1971221    /usr/lib/i386-linux-gnu/libGL.so.1.0.0
 b75f5000-b75f6000 rw-p 0005f000 08:03 1971221    /usr/lib/i386-linux-gnu/libGL.so.1.0.0
 b75f6000-b763f000 r-xp 00000000 08:03 3807735    /usr/lib/xorg/modules/extensions/libglx.so
 b763f000-b7640000 r--p 00048000 08:03 3807735    /usr/lib/xorg/modules/extensions/libglx.so
 b7640000-b7642000 rw-p 00049000 08:03 3807735    /usr/lib/xorg/modules/extensions/libglx.so
 b7642000-b7683000 rw-p 00000000 00:00 0 
 b7683000-b769f000 r-xp 00000000 08:03 5111822    /lib/i386-linux-gnu/libgcc_s.so.1
 b769f000-b76a0000 r--p 0001b000 08:03 5111822    /lib/i386-linux-gnu/libgcc_s.so.1
 b76a0000-b76a1000 rw-p 0001c000 08:03 5111822    /lib/i386-linux-gnu/libgcc_s.so.1
 b76a1000-b76a5000 rw-p 00000000 00:00 0 
 b76a5000-b76dd000 r-xp 00000000 08:03 1973443    /usr/lib/i386-linux-gnu/libpng16.so.16.34.0
 b76dd000-b76de000 r--p 00037000 08:03 1973443    /usr/lib/i386-linux-gnu/libpng16.so.16.34.0
 b76de000-b76df000 rw-p 00038000 08:03 1973443    /usr/lib/i386-linux-gnu/libpng16.so.16.34.0
 b76df000-b76e3000 r-xp 00000000 08:03 5111813    /lib/i386-linux-gnu/libcap-ng.so.0.0.0
 b76e3000-b76e4000 r--p 00003000 08:03 5111813    /lib/i386-linux-gnu/libcap-ng.so.0.0.0
 b76e4000-b76e5000 rw-p 00004000 08:03 5111813    /lib/i386-linux-gnu/libcap-ng.so.0.0.0
 b76e5000-b76f9000 r-xp 00000000 08:03 1966720    /usr/lib/i386-linux-gnu/liblz4.so.1.7.1
 b76f9000-b76fa000 r--p 00013000 08:03 1966720    /usr/lib/i386-linux-gnu/liblz4.so.1.7.1
 b76fa000-b76fb000 rw-p 00014000 08:03 1966720    /usr/lib/i386-linux-gnu/liblz4.so.1.7.1
 b76fb000-b7724000 r-xp 00000000 08:03 5111875    /lib/i386-linux-gnu/liblzma.so.5.2.2
 b7724000-b7725000 ---p 00029000 08:03 5111875    /lib/i386-linux-gnu/liblzma.so.5.2.2
 b7725000-b7726000 r--p 00029000 08:03 5111875    /lib/i386-linux-gnu/liblzma.so.5.2.2
 b7726000-b7727000 rw-p 0002a000 08:03 5111875    /lib/i386-linux-gnu/liblzma.so.5.2.2
 b7727000-b77de000 r-xp 00000000 08:03 1973446    /usr/lib/i386-linux-gnu/libfreetype.so.6.15.0
 b77de000-b77df000 ---p 000b7000 08:03 1973446    /usr/lib/i386-linux-gnu/libfreetype.so.6.15.0
 b77df000-b77e3000 r--p 000b7000 08:03 1973446    /usr/lib/i386-linux-gnu/libfreetype.so.6.15.0
 b77e3000-b77e4000 rw-p 000bb000 08:03 1973446    /usr/lib/i386-linux-gnu/libfreetype.so.6.15.0
 b77e4000-b77ea000 r-xp 00000000 08:03 1977316    /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b77ea000-b77eb000 r--p 00005000 08:03 1977316    /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b77eb000-b77ec000 rw-p 00006000 08:03 1977316    /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b77ec000-b77fb000 r-xp 00000000 08:03 5111921    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b77fb000-b77fc000 r--p 0000e000 08:03 5111921    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b77fc000-b77fd000 rw-p 0000f000 08:03 5111921    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b77fd000-b781a000 r-xp 00000000 08:03 5111974    /lib/i386-linux-gnu/libz.so.1.2.11
 b781a000-b781b000 r--p 0001c000 08:03 5111974    /lib/i386-linux-gnu/libz.so.1.2.11
 b781b000-b781c000 rw-p 0001d000 08:03 5111974    /lib/i386-linux-gnu/libz.so.1.2.11
 b781c000-b781e000 rw-p 00000000 00:00 0 
 b781e000-b7834000 r-xp 00000000 08:03 5111873    /lib/i386-linux-gnu/libgpg-error.so.0.22.0
 b7834000-b7835000 r--p 00015000 08:03 5111873    /lib/i386-linux-gnu/libgpg-error.so.0.22.0
 b7835000-b7836000 rw-p 00016000 08:03 5111873    /lib/i386-linux-gnu/libgpg-error.so.0.22.0
 b7836000-b78ab000 r-xp 00000000 08:03 5111898    /lib/i386-linux-gnu/libpcre.so.3.13.3
 b78ab000-b78ac000 r--p 00074000 08:03 5111898    /lib/i386-linux-gnu/libpcre.so.3.13.3
 b78ac000-b78ad000 rw-p 00075000 08:03 5111898    /lib/i386-linux-gnu/libpcre.so.3.13.3
 b78ad000-b78b5000 r-xp 00000000 08:03 5111848    /lib/i386-linux-gnu/librt-2.27.so
 b78b5000-b78b6000 r--p 00007000 08:03 5111848    /lib/i386-linux-gnu/librt-2.27.so
 b78b6000-b78b7000 rw-p 00008000 08:03 5111848    /lib/i386-linux-gnu/librt-2.27.so
 b78b7000-b7a8c000 r-xp 00000000 08:03 5111832    /lib/i386-linux-gnu/libc-2.27.so
 b7a8c000-b7a8d000 ---p 001d5000 08:03 5111832    /lib/i386-linux-gnu/libc-2.27.so
 b7a8d000-b7a8f000 r--p 001d5000 08:03 5111832    /lib/i386-linux-gnu/libc-2.27.so
 b7a8f000-b7a90000 rw-p 001d7000 08:03 5111832    /lib/i386-linux-gnu/libc-2.27.so
 b7a90000-b7a93000 rw-p 00000000 00:00 0 
 b7a93000-b7aae000 r-xp 00000000 08:03 5111846    /lib/i386-linux-gnu/libpthread-2.27.so
 b7aae000-b7aaf000 r--p 0001a000 08:03 5111846    /lib/i386-linux-gnu/libpthread-2.27.so
 b7aaf000-b7ab0000 rw-p 0001b000 08:03 5111846    /lib/i386-linux-gnu/libpthread-2.27.so
 b7ab0000-b7ab2000 rw-p 00000000 00:00 0 
 b7ab2000-b7acb000 r-xp 00000000 08:03 5112019    /lib/i386-linux-gnu/libbsd.so.0.8.7
 b7acb000-b7acc000 r--p 00018000 08:03 5112019    /lib/i386-linux-gnu/libbsd.so.0.8.7
 b7acc000-b7acd000 rw-p 00019000 08:03 5112019    /lib/i386-linux-gnu/libbsd.so.0.8.7
 b7acd000-b7bcd000 r-xp 00000000 08:03 5111836    /lib/i386-linux-gnu/libm-2.27.so
 b7bcd000-b7bce000 r--p 000ff000 08:03 5111836    /lib/i386-linux-gnu/libm-2.27.so
 b7bce000-b7bcf000 rw-p 00100000 08:03 5111836    /lib/i386-linux-gnu/libm-2.27.so
 b7bcf000-b7bed000 r-xp 00000000 08:03 5111817    /lib/i386-linux-gnu/libaudit.so.1.0.0
 b7bed000-b7bee000 r--p 0001d000 08:03 5111817    /lib/i386-linux-gnu/libaudit.so.1.0.0
 b7bee000-b7bef000 rw-p 0001e000 08:03 5111817    /lib/i386-linux-gnu/libaudit.so.1.0.0
 b7bef000-b7bf9000 rw-p 00000000 00:00 0 
 b7bf9000-b7bfe000 r-xp 00000000 08:03 1972918    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b7bfe000-b7bff000 r--p 00004000 08:03 1972918    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b7bff000-b7c00000 rw-p 00005000 08:03 1972918    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b7c00000-b7c01000 r-xp 00000000 08:03 1977095    /usr/lib/i386-linux-gnu/libxshmfence.so.1.0.0
 b7c01000-b7c02000 r--p 00000000 08:03 1977095    /usr/lib/i386-linux-gnu/libxshmfence.so.1.0.0
 b7c02000-b7c03000 rw-p 00001000 08:03 1977095    /usr/lib/i386-linux-gnu/libxshmfence.so.1.0.0
 b7c03000-b7c90000 r-xp 00000000 08:03 5111997    /lib/i386-linux-gnu/libsystemd.so.0.21.0
 b7c90000-b7c92000 r--p 0008c000 08:03 5111997    /lib/i386-linux-gnu/libsystemd.so.0.21.0
 b7c92000-b7c93000 rw-p 0008e000 08:03 5111997    /lib/i386-linux-gnu/libsystemd.so.0.21.0
 b7c93000-b7c95000 rw-p 00000000 00:00 0 
 b7c95000-b7c97000 r-xp 00000000 08:03 1972916    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b7c97000-b7c98000 r--p 00001000 08:03 1972916    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b7c98000-b7c99000 rw-p 00002000 08:03 1972916    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b7c99000-b7cc7000 r-xp 00000000 08:03 1978340    /usr/lib/i386-linux-gnu/libXfont2.so.2.0.0
 b7cc7000-b7cc8000 r--p 0002d000 08:03 1978340    /usr/lib/i386-linux-gnu/libXfont2.so.2.0.0
 b7cc8000-b7cc9000 rw-p 0002e000 08:03 1978340    /usr/lib/i386-linux-gnu/libXfont2.so.2.0.0
 b7cc9000-b7d71000 r-xp 00000000 08:03 1973510    /usr/lib/i386-linux-gnu/libpixman-1.so.0.34.0
 b7d71000-b7d77000 r--p 000a7000 08:03 1973510    /usr/lib/i386-linux-gnu/libpixman-1.so.0.34.0
 b7d77000-b7d78000 rw-p 000ad000 08:03 1973510    /usr/lib/i386-linux-gnu/libpixman-1.so.0.34.0
 b7d78000-b7d8a000 r-xp 00000000 08:03 1974022    /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7d8a000-b7d8b000 r--p 00011000 08:03 1974022    /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7d8b000-b7d8c000 rw-p 00012000 08:03 1974022    /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7d8c000-b7d95000 r-xp 00000000 08:03 1974287    /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b7d95000-b7d96000 ---p 00009000 08:03 1974287    /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b7d96000-b7d97000 r--p 00009000 08:03 1974287    /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b7d97000-b7d98000 rw-p 0000a000 08:03 1974287    /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b7d98000-b7d9b000 r-xp 00000000 08:03 5111835    /lib/i386-linux-gnu/libdl-2.27.so
 b7d9b000-b7d9c000 r--p 00002000 08:03 5111835    /lib/i386-linux-gnu/libdl-2.27.so
 b7d9c000-b7d9d000 rw-p 00003000 08:03 5111835    /lib/i386-linux-gnu/libdl-2.27.so
 b7d9d000-b7e78000 r-xp 00000000 08:03 5111977    /lib/i386-linux-gnu/libgcrypt.so.20.2.1
 b7e78000-b7e79000 ---p 000db000 08:03 5111977    /lib/i386-linux-gnu/libgcrypt.so.20.2.1
 b7e79000-b7e7a000 r--p 000db000 08:03 5111977    /lib/i386-linux-gnu/libgcrypt.so.20.2.1
 b7e7a000-b7e7d000 rw-p 000dc000 08:03 5111977    /lib/i386-linux-gnu/libgcrypt.so.20.2.1
 b7e7d000-b7e7e000 rw-p 00000000 00:00 0 
 b7e7e000-b7ea7000 r-xp 00000000 08:03 5111904    /lib/i386-linux-gnu/libselinux.so.1
 b7ea7000-b7ea8000 r--p 00028000 08:03 5111904    /lib/i386-linux-gnu/libselinux.so.1
 b7ea8000-b7ea9000 rw-p 00029000 08:03 5111904    /lib/i386-linux-gnu/libselinux.so.1
 b7ea9000-b7eaa000 rw-p 00000000 00:00 0 
 b7eaa000-b7ec9000 r-xp 00000000 08:03 5112400    /lib/i386-linux-gnu/libudev.so.1.6.9
 b7ec9000-b7eca000 r--p 0001e000 08:03 5112400    /lib/i386-linux-gnu/libudev.so.1.6.9
 b7eca000-b7ecb000 rw-p 0001f000 08:03 5112400    /lib/i386-linux-gnu/libudev.so.1.6.9
 b7ecb000-b7f24000 r-xp 00000000 08:03 5111886    /lib/i386-linux-gnu/libdbus-1.so.3.19.4
 b7f24000-b7f25000 r--p 00058000 08:03 5111886    /lib/i386-linux-gnu/libdbus-1.so.3.19.4
 b7f25000-b7f26000 rw-p 00059000 08:03 5111886    /lib/i386-linux-gnu/libdbus-1.so.3.19.4
 b7f26000-b7f27000 rwxp 00000000 00:00 0 
 b7f27000-b7f2c000 r-xp 00000000 08:03 3546460    /usr/lib/xorg/modules/drivers/fbdev_drv.so
 b7f2c000-b7f2d000 r--p 00004000 08:03 3546460    /usr/lib/xorg/modules/drivers/fbdev_drv.so
 b7f2d000-b7f2e000 rw-p 00005000 08:03 3546460    /usr/lib/xorg/modules/drivers/fbdev_drv.so
 b7f2e000-b7f3a000 r-xp 00000000 08:03 1977110    /usr/lib/i386-linux-gnu/libdrm_radeon.so.1.0.1
 b7f3a000-b7f3b000 r--p 0000b000 08:03 1977110    /usr/lib/i386-linux-gnu/libdrm_radeon.so.1.0.1
 b7f3b000-b7f3c000 rw-p 0000c000 08:03 1977110    /usr/lib/i386-linux-gnu/libdrm_radeon.so.1.0.1
 b7f3c000-b7f3e000 r-xp 00000000 08:03 3546459    /usr/lib/xorg/modules/drivers/ati_drv.so
 b7f3e000-b7f3f000 r--p 00001000 08:03 3546459    /usr/lib/xorg/modules/drivers/ati_drv.so
 b7f3f000-b7f40000 rw-p 00002000 08:03 3546459    /usr/lib/xorg/modules/drivers/ati_drv.so
 b7f40000-b7f42000 rw-p 00000000 00:00 0 
 b7f42000-b7f45000 r--p 00000000 00:00 0          [vvar]
 b7f45000-b7f47000 r-xp 00000000 00:00 0          [vdso]
 b7f47000-b7f6d000 r-xp 00000000 08:03 5111823    /lib/i386-linux-gnu/ld-2.27.so
 b7f6d000-b7f6e000 r--p 00025000 08:03 5111823    /lib/i386-linux-gnu/ld-2.27.so
 b7f6e000-b7f6f000 rw-p 00026000 08:03 5111823    /lib/i386-linux-gnu/ld-2.27.so
 bfcaa000-bfccb000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:	Xorg
 Umask:	0022
 State:	S (sleeping)
 Tgid:	680
 Ngid:	0
 Pid:	680
 PPid:	666
 TracerPid:	0
 Uid:	0	0	0	0
 Gid:	0	0	0	0
 FDSize:	32
 Groups:	 
 NStgid:	680
 NSpid:	680
 NSpgid:	680
 NSsid:	680
 VmPeak:	  158588 kB
 VmSize:	  158588 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	   43776 kB
 VmRSS:	   43776 kB
 RssAnon:	   13336 kB
 RssFile:	   30440 kB
 RssShmem:	       0 kB
 VmData:	   40040 kB
 VmStk:	     132 kB
 VmExe:	    2516 kB
 VmLib:	  109600 kB
 VmPTE:	     288 kB
 VmSwap:	       0 kB
 HugetlbPages:	       0 kB
 CoreDumping:	1
 Threads:	1
 SigQ:	0/25288
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	000000000a392000
 SigIgn:	0000000000001000
 SigCgt:	00000001c18066cf
 CapInh:	0000000000000000
 CapPrm:	0000003fffffffff
 CapEff:	0000003fffffffff
 CapBnd:	0000003fffffffff
 CapAmb:	0000000000000000
 NoNewPrivs:	0
 Seccomp:	0
 Speculation_Store_Bypass:	vulnerable
 Cpus_allowed:	3
 Cpus_allowed_list:	0-1
 Mems_allowed:	1
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	1106
 nonvoluntary_ctxt_switches:	146
Signal: 6
Uname: Linux 4.15.0-106-generic i686
UserGroups:
```

---

### Post by guiverc on 2020-06-13
> **libertyspike138 said:**
> Hello, I recently did a fresh install of Xubuntu Core 18.04 32 bit on my old P4 machine.
..
I also checked to see if I could upgrade to a newer version of lightdm but 1.30 has some dependencies that are not available until version 19.04 and it is 64 bit only.


You mention changing video cards - did you re-install? or make any changes on changing video card (I have little experience on changing cards, but I've ended up re-installing..).

[I]I have a pentium 4 system that is used for testing, and as it was used for testing both Lubuntu and Xubuntu through 19.04 cycles, so I know i386 binaries/packages were built  (I bumped one of my installs (three hdds and I had six installs) to eoan/19.10 and watched the infrastructure stop producing binaries on eoan as it fell behind my x86_64 systems, but 19.04 always kept current - alas it is now EOL/end-of-life)

I just booted a Lubuntu 19.04/disco (alpha) x86/i386 thumb-drive I never wiped on my pentium 4 x86 system, and modified it to deal with EOL status, and it reports 1122 packages to upgrade, 123 to new install, need to get 913MB of archives (489MB of additional disk space will be used), so packages sure seem to still be there... I `apt install mousepad` (as it's small) and it downloaded and installed 3 disco/universe packages.. [/I]*so packages sure seem to still be there...  **Should you use them, I don't know, but I'd really look for better solutions...*

---

### Post by libertyspike138 on 2020-06-13
> **guiverc said:**
> You mention changing video cards - did you re-install? or make any changes on changing video card (I have little experience on changing cards, but I've ended up re-installing..).

[I]I have a pentium 4 system that is used for testing, and as it was used for testing both Lubuntu and Xubuntu through 19.04 cycles, so I know i386 binaries/packages were built  (I bumped one of my installs (three hdds and I had six installs) to eoan/19.10 and watched the infrastructure stop producing binaries on eoan as it fell behind my x86_64 systems, but 19.04 always kept current - alas it is now EOL/end-of-life)

I just booted a Lubuntu 19.04/disco (alpha) x86/i386 thumb-drive I never wiped on my pentium 4 x86 system, and modified it to deal with EOL status, and it reports 1122 packages to upgrade, 123 to new install, need to get 913MB of archives (489MB of additional disk space will be used), so packages sure seem to still be there... I `apt install mousepad` (as it's small) and it downloaded and installed 3 disco/universe packages.. [/I]*so packages sure seem to still be there...  **Should you use them, I don't know, but I'd really look for better solutions...*

---

Both the GeForce 6200 and Radeon 9250 have both a VGA port that I run through my KVM with my main machine as well as as a DVI port where I hooked it up to my old CRT TV that I use for working on game consoles. Being a CRT TV it is is nice to be able to test things that require it like Nintendo Zappers while also being able to do 720p and 1080p but the TV was made with overscan that you cannot turn off so over a desktop icons worth of the picture is cutoff of each side of the screen. By default the screens are mirrored and I usually keep it in the default of 1280X720 but also like to add 1280x960 to my xprofile because my monitor can do both and when I switch to this resolution the whole screen is displayed on the TV, it is just in 3:4 instead so there are black lines on each side of the TV but the whole desktop is there while everything looks OK on my monitor in either resolution. I don't remember what my initial complaints were with the nouveau driver on the GeForce but something was not working properly. I then found a patch to change the 16.04 compatible binary from nVidia to install under 18.04 and all went well with the installation but the max resolution nvida-settings gave me was 960X540 and there were no options to assign custom resolutions like in the Windows version of the driver software. I then remembered that I had one other AGP card in my stash so I ran the nVidia uninstaller to get nouveau back and proceeded to install that Radeon card. It worked properly right away with the nouveau drivers defaulting to a mirror on 1280X720 with the ability to add 1280X960 to my xprofile and no issues switching.

I have been using Ubuntu for over a decade and prefer to stick with LTS releases as I have had some issues with the releases in between in the past. Initially they said that 16.04 was going to be the last 32 bit release but I recently found the 32 bit network installer for 18.04 so that is what I went with on this machine. I downloaded the upgraded lightdm 1.30 package from one of the future distros to check it and there were dependencies not available. For example it wanted a newer version of libc6 but libc6 has several more dependencies that it wants etc. I also checked synaptic to see if I could force an older version of lightdm in case it is a bug with that specific release but the version installed was the only option.

I will also note that after I wrote this I got 2 more reboots with no crash so it is intermittent and crashes at startup when it feels like. Everything seems to boot fine but it is annoying to have the system problem detected pop-up sometimes right after logging in.

---

### Post by CelticWarrior on 2020-06-13
Any 18.04 flavor has support until April next years only. The standard Ubuntu LTS has 5 years of support but flavors only 3.
I suggest you start thinking and experimenting with something that will carry on 32-bit support for some time longer (how much longer is anyone's guess) like Debian.

---

### Post by libertyspike138 on 2020-06-14
> **CelticWarrior said:**
> Any 18.04 flavor has support until April next years only. The standard Ubuntu LTS has 5 years of support but flavors only 3.
I suggest you start thinking and experimenting with something that will carry on 32-bit support for some time longer (how much longer is anyone's guess) like Debian.

I had initially installed Debian considering even the latest still has 32 bit builds but was not impressed comparing it to my main machine running Ubuntu 18.04. I had to go out of my way to get a few of the programs I usually use whereas there are PPAs available under Ubuntu. Then out of nowhere it just completely froze. Considering I had just installed it I decided that if it is going to freeze on me there are obviously some bugs that need to be worked out and decided to go with what I would usually go with on an older system which is Lubuntu or Xubuntu. I ultimately decided on Xubuntu because I do not like all the changes in the latest Lubuntu which I used for years. It is not as polished as Xubuntu and heavily relies on QT now. Then there was the other issue of how I usually do custom builds from the mini network installer. Starting with 18.04 you can no longer install lubuntu-core aka minimal, only full lubuntu-desktop or lxde-core. Even with previous builds I usually prefer Ubuntu over Debian because there always seems to be more support and more packages readily available.

---

### Post by guiverc on 2020-06-14
> **libertyspike138 said:**
> I had initially installed Debian considering even the latest still has 32 bit builds but was not impressed comparing it to my main machine running Ubuntu 18.04. I had to go out of my way to get a few of the programs I usually use whereas there are PPAs available under Ubuntu.  ..  decided to go with what I would usually go with on an older system which is Lubuntu or Xubuntu.

 I ultimately decided on Xubuntu because I do not like all the changes in the latest Lubuntu which I used for years. It is not as polished as Xubuntu and heavily relies on QT now. Then there was the other issue of how I usually do custom builds from the mini network installer. Starting with 18.04 you can no longer install lubuntu-core aka minimal, only full lubuntu-desktop or lxde-core. Even with previous builds I usually prefer Ubuntu over Debian because there always seems to be more support and more packages readily available.


I have no issues with debian, find it almost as easy to Ubuntu truthfully, but it's also where I started (Ubuntu didn't start until 2004). I use debian too (*inc. on i586 boxes that can't run any supported Ubuntu*)

Yes Lubuntu announced they were moving to LXQt (*as many developers of LXDE had announced they were joining with Razor-Qt team and creating a new LXQt desktop*) but I don't see any other choice.  Lubuntu itself created Lubuntu-Next for testing purposes, but LXQt wasn't introduced into Lubuntu until the 18.10 cycle.  You were only talking about 18.04 LTS which used the old LXDE (legacy Lubuntu); Lubuntu 18.04 LTS has no Qt in it.

The `lubuntu-core` package exists for all LXDE/legacy Lubuntu releases - ie. [https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=lubuntu-core](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=lubuntu-core) where you'll note it includes releases up to (*and including*) 18.04 LTS

As you find Xubuntu *more polished* stick with it (I wouldn't have tested Xubuntu if I didn't like it too; the only reason I mentioned Lubuntu 19.04 [x86] ISO was I'd overwritten the Xubuntu x86 one with a 18.04.4 image).  Both Xubuntu and Lubuntu dropped x86 in the same month (one and a half cycles after other flavors did; why i have x86 ISOs for them)

---

### Post by libertyspike138 on 2020-06-15
> **guiverc said:**
> I have no issues with debian, find it almost as easy to Ubuntu truthfully, but it's also where I started (Ubuntu didn't start until 2004). I use debian too (*inc. on i586 boxes that can't run any supported Ubuntu*)

Yes Lubuntu announced they were moving to LXQt (*as many developers of LXDE had announced they were joining with Razor-Qt team and creating a new LXQt desktop*) but I don't see any other choice.  Lubuntu itself created Lubuntu-Next for testing purposes, but LXQt wasn't introduced into Lubuntu until the 18.10 cycle.  You were only talking about 18.04 LTS which used the old LXDE (legacy Lubuntu); Lubuntu 18.04 LTS has no Qt in it.

The `lubuntu-core` package exists for all LXDE/legacy Lubuntu releases - ie. [https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=lubuntu-core](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=lubuntu-core) where you'll note it includes releases up to (*and including*) 18.04 LTS

As you find Xubuntu *more polished* stick with it (I wouldn't have tested Xubuntu if I didn't like it too; the only reason I mentioned Lubuntu 19.04 [x86] ISO was I'd overwritten the Xubuntu x86 one with a 18.04.4 image).  Both Xubuntu and Lubuntu dropped x86 in the same month (one and a half cycles after other flavors did; why i have x86 ISOs for them)

---

My Linux journey started with Red Hat probably over 20 years ago now. I think I have been using Ubuntu since about 6.XX or so. I have used Debian on some ARM chips as it always seems to work out smoother there than other options. Anyway either my problem has resolved itself or I'm just too fast for the PC. :lol: After reaching the login screen I have been giving it a minute until the hdd light calms down before logging in and no more crash errors.

---

### Post by ajgreeny on 2020-06-15
Assuming the lxde DE is still available as an add-on package  you could try the 20.04 minimum install cd and make up your own Lubuntu equivalent

---

### Post by libertyspike138 on 2020-06-15
> **ajgreeny said:**
> Assuming the lxde DE is still available as an add-on package  you could try the 20.04 minimum install cd and make up your own Lubuntu equivalent

This is my old single core 32 bit Pentium 4 system. There are no 32 bit packages available for 20.04. My issue seems to have been resolved anyway. Besides I don't care much for Lubuntu now after all of the changes and all of the the QT stuff. GTK apps have always been more reliable for me than QT.

---

