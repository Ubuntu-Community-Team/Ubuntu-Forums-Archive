---
title: "Steam not running on Ubuntu 16.04 LTS"
date: 2018-05-16
forum: Gaming &amp; Leisure
---

### Post by narutimetto_93 on 2018-05-16
Hey guys, Recently I tried to run steam on my laptop after a while but it doesn't work.
After a few seconds of loading the app shuts down by itself and I don't get why. I tried to look for things on Google but I'm definitely not a pro user and I didn't manage to find something useful.
It should be a problem of libraries but I don't much more about it. (Sorry for the bad English but I'm an Italian user).

Thank you in advance for your help.

This is what happen when I try to run Steam on the terminal 

```
malcom@malcom-X540LA:~$ steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2018-05-16 15:45:30] Startup - updater built Jun 16 2014 11:16:02
*** Error in `/home/malcom/.steam/ubuntu12_32/steam': munmap_chunk(): invalid pointer: 0xf75d5a48 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x67377)[0xf728c377]
/lib/i386-linux-gnu/libc.so.6(+0x6d2f7)[0xf72922f7]
/lib/i386-linux-gnu/libc.so.6(+0x6d9e9)[0xf72929e9]
/usr/lib/i386-linux-gnu/libX11.so.6(XFree+0x18)[0xf760c6d8]
/home/malcom/.steam/ubuntu12_32/steam(+0x43859)[0x56612859]
/home/malcom/.steam/ubuntu12_32/steam(+0x44034)[0x56613034]
/home/malcom/.steam/ubuntu12_32/steam(+0x14b74)[0x565e3b74]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf7)[0xf723d637]
/home/malcom/.steam/ubuntu12_32/steam(+0x18115)[0x565e7115]
======= Memory map: ========
565cf000-56828000 r-xp 00000000 08:01 17697125                           /home/malcom/.steam/ubuntu12_32/steam
56828000-56830000 r--p 00259000 08:01 17697125                           /home/malcom/.steam/ubuntu12_32/steam
56830000-56836000 rw-p 00261000 08:01 17697125                           /home/malcom/.steam/ubuntu12_32/steam
56836000-56858000 rw-p 00000000 00:00 0 
581fe000-58343000 rw-p 00000000 00:00 0                                  [heap]
f60ca000-f60d1000 r--s 00000000 08:01 14952121                           /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
f60d1000-f60db000 r-xp 00000000 08:01 14949713                           /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
f60db000-f60dc000 r--p 00009000 08:01 14949713                           /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
f60dc000-f60dd000 rw-p 0000a000 08:01 14949713                           /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
f60dd000-f60e9000 r-xp 00000000 08:01 14942349                           /usr/lib/i386-linux-gnu/libdrm_radeon.so.1.0.1
f60e9000-f60ea000 r--p 0000b000 08:01 14942349                           /usr/lib/i386-linux-gnu/libdrm_radeon.so.1.0.1
f60ea000-f60eb000 rw-p 0000c000 08:01 14942349                           /usr/lib/i386-linux-gnu/libdrm_radeon.so.1.0.1
f60eb000-f60f3000 r-xp 00000000 08:01 14942347                           /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
f60f3000-f60f4000 r--p 00007000 08:01 14942347                           /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
f60f4000-f60f5000 rw-p 00008000 08:01 14942347                           /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0
f60f5000-f611a000 r-xp 00000000 08:01 14942345                           /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
f611a000-f611b000 r--p 00024000 08:01 14942345                           /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
f611b000-f611c000 rw-p 00025000 08:01 14942345                           /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
f611c000-f6135000 r-xp 00000000 08:01 14553636                           /lib/i386-linux-gnu/libz.so.1.2.8
f6135000-f6136000 r--p 00018000 08:01 14553636                           /lib/i386-linux-gnu/libz.so.1.2.8
f6136000-f6137000 rw-p 00019000 08:01 14553636                           /lib/i386-linux-gnu/libz.so.1.2.8
f6137000-f6a45000 r-xp 00000000 08:01 14942335                           /usr/lib/i386-linux-gnu/dri/i965_dri.so
f6a45000-f6a46000 ---p 0090e000 08:01 14942335                           /usr/lib/i386-linux-gnu/dri/i965_dri.so
f6a46000-f6a85000 r--p 0090e000 08:01 14942335                           /usr/lib/i386-linux-gnu/dri/i965_dri.so
f6a85000-f6a8b000 rw-p 0094d000 08:01 14942335                           /usr/lib/i386-linux-gnu/dri/i965_dri.so
f6a8b000-f6ad4000 rw-p 00000000 00:00 0 
f6ad4000-f6ae6000 r-xp 00000000 08:01 14942455                           /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
f6ae6000-f6ae7000 r--p 00011000 08:01 14942455                           /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
f6ae7000-f6ae8000 rw-p 00012000 08:01 14942455                           /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
f6ae8000-f6aed000 r-xp 00000000 08:01 14949484                           /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
f6aed000-f6aee000 r--p 00004000 08:01 14949484                           /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
f6aee000-f6aef000 rw-p 00005000 08:01 14949484                           /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
f6aef000-f6af3000 r-xp 00000000 08:01 14949734                           /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
f6af3000-f6af4000 r--p 00003000 08:01 14949734                           /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
f6af4000-f6af5000 rw-p 00004000 08:01 14949734                           /usr/lib/i386-linux-gnu/libxcb-dri2.so.0.0.0
f6af5000-f6b0d000 r-xp 00000000 08:01 14949738                           /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
f6b0d000-f6b0e000 ---p 00018000 08:01 14949738                           /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
f6b0e000-f6b0f000 r--p 00018000 08:01 14949738                           /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
f6b0f000-f6b10000 rw-p 00019000 08:01 14949738                           /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
f6b10000-f6b23000 r-xp 00000000 08:01 14949448                           /usr/lib/i386-linux-gnu/libXext.so.6.4.0
f6b23000-f6b24000 r--p 00012000 08:01 14949448                           /usr/lib/i386-linux-gnu/libXext.so.6.4.0
f6b24000-f6b25000 rw-p 00013000 08:01 14949448                           /usr/lib/i386-linux-gnu/libXext.so.6.4.0
f6b25000-f6b39000 r-xp 00000000 08:01 14942415                           /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
f6b39000-f6b3a000 ---p 00014000 08:01 14942415                           /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
f6b3a000-f6b3c000 r--p 00014000 08:01 14942415                           /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
f6b3c000-f6b42000 rwxp 00016000 08:01 14942415                           /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
f6b42000-f6b43000 rwxp 00000000 00:00 0 
f6b43000-f6b69000 r-xp 00000000 08:01 14552515                           /lib/i386-linux-gnu/libexpat.so.1.6.0
f6b69000-f6b6a000 ---p 00026000 08:01 14552515                           /lib/i386-linux-gnu/libexpat.so.1.6.0
f6b6a000-f6b6c000 r--p 00026000 08:01 14552515                           /lib/i386-linux-gnu/libexpat.so.1.6.0
f6b6c000-f6b6d000 rw-p 00028000 08:01 14552515                           /lib/i386-linux-gnu/libexpat.so.1.6.0
f6b6d000-f6bd6000 r-xp 00000000 08:01 14942351                           /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
f6bd6000-f6bd8000 r--p 00068000 08:01 14942351                           /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
f6bd8000-f6bdd000 rwxp 0006a000 08:01 14942351                           /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
f6be0000-f6c02000 r--p 00000000 08:01 16779321                           /usr/share/locale-langpack/it/LC_MESSAGES/libc.mo
f6c02000-f6fd3000 rw-p 00000000 00:00 0 
f6fd3000-f71d3000 r--p 00000000 08:01 14813014                           /usr/lib/locale/locale-archive
f71d3000-f71d6000 rw-p 00000000 00:00 0 
f71d6000-f71db000 r-xp 00000000 08:01 14949442                           /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f71db000-f71dc000 r--p 00004000 08:01 14949442                           /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f71dc000-f71dd000 rw-p 00005000 08:01 14949442                           /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
f71dd000-f71de000 rw-p 00000000 00:00 0 
f71de000-f71e0000 r-xp 00000000 08:01 14949440                           /usr/lib/i386-linux-gnu/libXau.so.6.0.0
f71e0000-f71e1000 r--p 00001000 08:01 14949440                           /usr/lib/i386-linux-gnu/libXau.so.6.0.0
f71e1000-f71e2000 rw-p 00002000 08:01 14949440                           /usr/lib/i386-linux-gnu/libXau.so.6.0.0
f71e2000-f71fe000 r-xp 00000000 08:01 14549076                           /lib/i386-linux-gnu/libgcc_s.so.1
f71fe000-f71ff000 rw-p 0001b000 08:01 14549076                           /lib/i386-linux-gnu/libgcc_s.so.1
f71ff000-f7223000 r-xp 00000000 08:01 14949444                           /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
f7223000-f7224000 r--p 00023000 08:01 14949444                           /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
f7224000-f7225000 rw-p 00024000 08:01 14949444                           /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
f7225000-f73d5000 r-xp 00000000 08:01 14552674                           /lib/i386-linux-gnu/libc-2.23.so
f73d5000-f73d7000 r--p 001af000 08:01 14552674                           /lib/i386-linux-gnu/libc-2.23.so
f73d7000-f73d8000 rw-p 001b1000 08:01 14552674                           /lib/i386-linux-gnu/libc-2.23.so
f73d8000-f73db000 rw-p 00000000 00:00 0 
f73db000-f73f4000 r-xp 00000000 08:01 14550041                           /lib/i386-linux-gnu/libpthread-2.23.so
f73f4000-f73f5000 r--p 00018000 08:01 14550041                           /lib/i386-linux-gnu/libpthread-2.23.so
f73f5000-f73f6000 rw-p 00019000 08:01 14550041                           /lib/i386-linux-gnu/libpthread-2.23.so
f73f6000-f73f9000 rw-p 00000000 00:00 0 
f73f9000-f7566000 r-xp 00000000 08:01 14942219                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.21
f7566000-f7567000 ---p 0016d000 08:01 14942219                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.21
f7567000-f756c000 r--p 0016d000 08:01 14942219                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.21
f756c000-f756d000 rw-p 00172000 08:01 14942219                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.21
f756d000-f7570000 rw-p 00000000 00:00 0 
f7570000-f7573000 r-xp 00000000 08:01 14552680                           /lib/i386-linux-gnu/libdl-2.23.so
f7573000-f7574000 r--p 00002000 08:01 14552680                           /lib/i386-linux-gnu/libdl-2.23.so
f7574000-f7575000 rw-p 00003000 08:01 14552680                           /lib/i386-linux-gnu/libdl-2.23.so
f7575000-f75c8000 r-xp 00000000 08:01 14549084                           /lib/i386-linux-gnu/libm-2.23.so
f75c8000-f75c9000 r--p 00052000 08:01 14549084                           /lib/i386-linux-gnu/libm-2.23.so
f75c9000-f75ca000 rw-p 00053000 08:01 14549084                           /lib/i386-linux-gnu/libm-2.23.so
f75ca000-f75d1000 r-xp 00000000 08:01 14553119                           /lib/i386-linux-gnu/librt-2.23.so
f75d1000-f75d2000 r--p 00006000 08:01 14553119                           /lib/i386-linux-gnu/librt-2.23.so
f75d2000-f75d3000 rw-p 00007000 08:01 14553119                           /lib/i386-linux-gnu/librt-2.23.so
f75d3000-f7719000 r-xp 00000000 08:01 14949446                           /usr/lib/i386-linux-gnu/libX11.so.6.3.0
f7719000-f771a000 ---p 00146000 08:01 14949446                           /usr/lib/i386-linux-gnu/libX11.so.6.3.0
f771a000-f771b000 r--p 00146000 08:01 14949446                           /usr/lib/i386-linux-gnu/libX11.so.6.3.0
f771b000-f771d000 rw-p 00147000 08:01 14949446                           /usr/lib/i386-linux-gnu/libX11.so.6.3.0
f771d000-f771e000 rw-p 00000000 00:00 0 
f771f000-f7720000 rw-p 00000000 00:00 0 
f7720000-f7721000 r-xp 00000000 08:01 14949732                           /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
f7721000-f7722000 r--p 00000000 08:01 14949732                           /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
f7722000-f7723000 rw-p 00001000 08:01 14949732                           /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
f7723000-f7728000 r-xp 00000000 08:01 14949476                           /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
f7728000-f7729000 r--p 00004000 08:01 14949476                           /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
f7729000-f772a000 rw-p 00005000 08:01 14949476                           /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
f772a000-f772c000 r-xp 00000000 08:01 14949474                           /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
f772c000-f772d000 r--p 00001000 08:01 14949474                           /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
f772d000-f772e000 rw-p 00002000 08:01 14949474                           /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
f772e000-f772f000 r-xp 00000000 08:01 14949478                           /usr/lib/i386-linux-gnu/libxshmfence.so.1.0.0
f772f000-f7730000 r--p 00000000 08:01 14949478                           /usr/lib/i386-linux-gnu/libxshmfence.so.1.0.0
f7730000-f7731000 rw-p 00001000 08:01 14949478                           /usr/lib/i386-linux-gnu/libxshmfence.so.1.0.0
f7731000-f7736000 r-xp 00000000 08:01 14949742                           /usr/lib/i386-linux-gnu/libxcb-sync.so.1.0.0
f7736000-f7737000 ---p 00005000 08:01 14949742                           /usr/lib/i386-linux-gnu/libxcb-sync.so.1.0.0
f7737000-f7738000 r--p 00005000 08:01 14949742                           /usr/lib/i386-linux-gnu/libxcb-sync.so.1.0.0
f7738000-f7739000 rw-p 00006000 08:01 14949742                           /usr/lib/i386-linux-gnu/libxcb-sync.so.1.0.0
f7739000-f773b000 r-xp 00000000 08:01 14949740                           /usr/lib/i386-linux-gnu/libxcb-present.so.0.0.0
f773b000-f773c000 r--p 00001000 08:01 14949740                           /usr/lib/i386-linux-gnu/libxcb-present.so.0.0.0
f773c000-f773d000 rw-p 00002000 08:01 14949740                           /usr/lib/i386-linux-gnu/libxcb-present.so.0.0.0
f773d000-f773f000 r-xp 00000000 08:01 14949736                           /usr/lib/i386-linux-gnu/libxcb-dri3.so.0.0.0
f773f000-f7740000 r--p 00001000 08:01 14949736                           /usr/lib/i386-linux-gnu/libxcb-dri3.so.0.0.0
f7740000-f7741000 rw-p 00002000 08:01 14949736                           /usr/lib/i386-linux-gnu/libxcb-dri3.so.0.0.0
f7741000-f7742000 r--p 002d4000 08:01 14813014                           /usr/lib/locale/locale-archive
f7742000-f7743000 r--p 002de000 08:01 14813014                           /usr/lib/locale/locale-archive
f7743000-f7744000 rw-p 00000000 00:00 0 
f7744000-f7747000 r--p 00000000 00:00 0                                  [vvar]
f7747000-f7748000 r-xp 00000000 00:00 0                                  [vdso]
f7748000-f776b000 r-xp 00000000 08:01 14550037                           /lib/i386-linux-gnu/ld-2.23.so
f776b000-f776c000 r--p 00022000 08:01 14550037                           /lib/i386-linux-gnu/ld-2.23.so
f776c000-f776d000 rw-p 00023000 08:01 14550037                           /lib/i386-linux-gnu/ld-2.23.so
ffaf5000-ffb16000 rw-p 00000000 00:00 0                                  [stack]
Aborted (core dumped)


```

---

### Post by deadflowr on 2018-05-16
*Thread moved to **Gaming and Leisure***

---

### Post by Perfect Storm on 2018-05-17
Try uninstall and reinstall steam.

```
sudo apt remove --purge steam
rm -rf ~/.steam
sudo apt install steam
```

---

### Post by narutimetto_93 on 2018-05-17
I tried with commands you sent me but it does the same.

---

### Post by oldrocker99 on 2018-05-17
You did install Steam from the repos, not the Steam website, right?

---

### Post by narutimetto_93 on 2018-05-20
> **oldrocker99 said:**
> You did install Steam from the repos, not the Steam website, right?

At the beginning I downloaded from the site but only recently I started to have issues with that and now, no matter what the procedure I use, the result is the same :(.
I tried again from the terminal by it doesn't work either.

---

### Post by Richard_Romick on 2018-05-26
What kind of graphics card are you using and are you using the open-source or proprietary drivers?

---

