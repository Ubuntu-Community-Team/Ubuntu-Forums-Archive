---
title: "Problems with Steam"
date: 2016-05-09
forum: Gaming &amp; Leisure
---

### Post by valereguerin on 2016-05-09
[16.04 gnome]("https://wirejungle.wordpress.com/2015/01/09/how-to-fix-broken-steam-linux-client-with-radeon-graphics-driver-workaround/")

```
Code: LD_PRELOAD='/usr/$LIB/libstdc++.so.6' DIAPLAY=:0 steam 
```

:sad::sad::sad:i put this command-line in the terminal after every update/upgrade.........:confused:

and now the steam window not appear on my desktop i must looking for it on another desktop !. ????                 and openGL is slow to launch 

radeon R9 : 
```
# dmesg : [ 4490.440330] [drm:si_dpm_set_power_state [radeon]] *ERROR* si_restrict_performance_levels_before_switch failed

freeman@Sniper-one:~$ inxi -b
System:    Host: Sniper-one Kernel: 4.5.0-040500rc7-generic x86_64 (64 bit) Desktop: Gnome 3.18.4
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2794 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.18.3 drivers: ati,vesa (unloaded: fbdev,radeon) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.8.0) GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: D-Link System DGE-528T Gigabit Ethernet Adapter driver: r8169
           Card-2: Realtek RTL8191SU 802.11n WLAN Adapter driver: r8712u
Drives:    HDD Total Size: 5751.2GB (4.1% used)
Info:      Processes: 339 Uptime: 3:12 Memory: 3083.7/7852.8MB Client: Shell (bash) inxi: 2.2.35
```

---

### Post by valereguerin on 2016-07-29
i upgrade for 16.10 this morning machine don't want start virtual Machine and steam too, marvellous !

---

### Post by MikeCyber on 2016-08-02
3D is to slow in VM or you need to install the graphics driver.

---

### Post by valereguerin on 2016-08-09
??? there isn't any fglrx drivers for 16.04......! and know i upgrade to 16.10 ! it's the same thing...
just 15.10 is good for steam...for me...

```
freeman@Sniper-one:~$ LD_PRELOAD='/usr/$LIB/libstdc++.so.6' DIAPLAY=:0 steam
Running Steam on ubuntu 16.10 64-bit
STEAM_RUNTIME is enabled automatically
/bin/bash: /home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
awk: /home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Installing breakpad exception handler for appid(steam)/version(1468023329)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast


```

```
freeman@Sniper-one:~$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libstdc++.so.6 DISPLAY=:0 steam
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Running Steam on ubuntu 16.10 64-bit
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
STEAM_RUNTIME is enabled automatically
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
/bin/bash: /home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
awk: /home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
Installing breakpad exception handler for appid(steam)/version(1468023329)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

```

---

### Post by howefield on 2016-08-09
> **valereguerin said:**
> just 15.10 is good for steam...for me...

or 14.04.5 which is supported till 2019 unlike 15.10 which has already reached "End of Life".

---

### Post by valereguerin on 2016-08-09
i put .steam in my home in the taste-bin, repair install =

```
  freeman@Sniper-one:~$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libstdc++.so.6 DISPLAY=:0 steam
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Repairing installation, linking /home/freeman/.steam/steam to /home/freeman/.local/share/Steam
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Running Steam on ubuntu 16.10 64-bit
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
STEAM_RUNTIME is enabled automatically
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
/bin/bash: /home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
awk: /home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libstdc++.so.6' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Installing breakpad exception handler for appid(steam)/version(1468023329)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

```

Hello Howefield ! yes it's better but all my 14.04 system are upgrade now in 16.04 and 16.10....
i play only on 15.10 ....

```
freeman@Sniper-one:~$ DISPLAY=:0 LIBGL_DEBUG=verbose steam
Running Steam on ubuntu 16.10 64-bit
STEAM_RUNTIME is enabled automatically
/bin/bash: /home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
awk: /home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
Installing breakpad exception handler for appid(steam)/version(1468023329)
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/radeonsi_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/radeonsi_dri.so
libGL: dlopen /usr/lib/i386-linux-gnu/dri/radeonsi_dri.so failed (/home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.21' not found (required by /usr/lib/i386-linux-gnu/dri/radeonsi_dri.so))
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/radeonsi_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/radeonsi_dri.so
libGL: dlopen ${ORIGIN}/dri/radeonsi_dri.so failed (${ORIGIN}/dri/radeonsi_dri.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type)
libGL: OpenDriver: trying /usr/lib/dri/tls/radeonsi_dri.so
libGL: OpenDriver: trying /usr/lib/dri/radeonsi_dri.so
libGL: dlopen /usr/lib/dri/radeonsi_dri.so failed (/usr/lib/dri/radeonsi_dri.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
libGL: dlopen /usr/lib/i386-linux-gnu/dri/swrast_dri.so failed (/home/freeman/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.21' not found (required by /usr/lib/i386-linux-gnu/dri/swrast_dri.so))
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/swrast_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/swrast_dri.so
libGL: dlopen ${ORIGIN}/dri/swrast_dri.so failed (${ORIGIN}/dri/swrast_dri.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type)
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
libGL: dlopen /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type)
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

```

---

