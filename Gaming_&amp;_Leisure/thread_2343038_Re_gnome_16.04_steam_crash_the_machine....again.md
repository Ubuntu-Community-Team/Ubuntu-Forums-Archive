---
title: "Re: gnome 16.04 steam crash the machine....again"
date: 2016-11-12
forum: Gaming &amp; Leisure
---

### Post by valereguerin on 2016-11-12
hello,

Krash ! "just reboot" issue....again and again.....

```
freeman@freeman-sniperone:~$ uname -a
Linux freeman-sniperone 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
freeman@freeman-sniperone:~$ gnome-shell --version


Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Using breakpad crash handler



Steam_SetMinidumpSteamID: Caching Steam ID: 76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID: Setting Steam ID: 76561198052678839
No cached sticky mapping in GetActionSetHandle. Native Steam Controller support won't work.
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 22906 for game ID 730

[1112/161645:ERROR:ssl_client_socket_openssl.cc(1149)] handshake failed; returned -1, SSL error code 1, net_error -107
[1112/161645:ERROR:ssl_client_socket_openssl.cc(1149)] handshake failed; returned -1, SSL error code 1, net_error -107
[1112/161645:ERROR:ssl_client_socket_openssl.cc(1149)] handshake failed; returned -1, SSL error code 1, net_error -107
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: boadgeojelhgndaghljhdicfkmllpafd
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://boadgeojelhgndaghljhdicfkmllpafd/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: dliochdbjfkdbacpmhlcpmleaejidimm
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://dliochdbjfkdbacpmhlcpmleaejidimm/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: enhhojjnijigcajfphajepfemndkmdlo
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://enhhojjnijigcajfphajepfemndkmdlo/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: fmfcbgogabcbclcofgocippekhfcmgfj
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fmfcbgogabcbclcofgocippekhfcmgfj/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: pkedcjkdefgpdelpbcmbmeomcjbeemfm
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://pkedcjkdefgpdelpbcmbmeomcjbeemfm/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: fjhoaacokmgbjemoflkofnenfaiekifl
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fjhoaacokmgbjemoflkofnenfaiekifl/cast_sender.js
```



GNOME Shell 3.18.5
Ubuntu  16.04 Gallium 0.4 on AMD TAHITI (DRM 2.43.0 / 4.4.0-47-generic, LLVM  3.8.0) CG Radeon R9 280 proc i7 930 gigabytes G1.sniper rev 1.0

error.log :

```
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"

(steam:18240): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

(steam:18240): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Adwaita/gtk-2.0/gtkrc:1163: error: unexpected identifier `direction', expected character `}'
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1476379980)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
[1112/161222:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
[1112/161222:ERROR:browser_main_loop.cc(217)] Running without the SUID sandbox! See https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20161013004706)
Installing breakpad exception handler for appid(steamwebhelper)/version(1476319626)
[1112/161222:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
Installing breakpad exception handler for appid(steamwebhelper)/version(20161013004706)
Installing breakpad exception handler for appid(steamwebhelper)/version(1476379980)
Installing breakpad exception handler for appid(steamwebhelper)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Generating new string page texture 7: 128x256, total string texture memory is 131,07 KB
Generating new string page texture 8: 48x256, total string texture memory is 180,22 KB
Generating new string page texture 9: 256x256, total string texture memory is 442,37 KB
Generating new string page texture 10: 64x256, total string texture memory is 507,90 KB
Generating new string page texture 11: 8x256, total string texture memory is 516,10 KB
Generating new string page texture 12: 16x256, total string texture memory is 532,48 KB
Generating new string page texture 13: 24x256, total string texture memory is 557,06 KB
Generating new string page texture 14: 32x256, total string texture memory is 589,82 KB
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
Installing breakpad exception handler for appid(steam)/version(1476379980)
roaming config store loaded successfully - 1247 bytes.
migrating temporary roaming config store
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1476379980)
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/freeman/.steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1476379980)
System startup time: 16,34 seconds
Generating new string page texture 97: 1024x256, total string texture memory is 1,64 MB
Generating new string page texture 98: 256x256, total string texture memory is 262,14 KB
Generating new string page texture 101: 384x256, total string texture memory is 2,03 MB
Generating new string page texture 102: 256x256, total string texture memory is 2,29 MB
Generating new string page texture 103: 128x256, total string texture memory is 2,42 MB
bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by bash)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
rm: cannot remove '/home/freeman/.steam/bin': Is a directory
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
awk: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
/usr/bin/ldd: line 119: printf: write error: Broken pipe
ExecCommandLine: "/home/freeman/.steam/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 126: 256x256, total string texture memory is 2,69 MB
Game update: AppID 730 "Counter-Strike: Global Offensive", ProcID 22470, IP 0.0.0.0:0
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 22470 for game ID 730
>>> Adding process 22471 for game ID 730
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
pid 22473 != 22472, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 22472 for game ID 730
>>> Adding process 22474 for game ID 730
>>> Adding process 22475 for game ID 730
Installing breakpad exception handler for appid(gameoverlayui)/version(20161013004725)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Using breakpad crash handler
Setting breakpad minidump AppID = 730
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
No cached sticky mapping in GetActionSetHandle. Native Steam Controller support won't work.
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 22906 for game ID 730
>>> Adding process 22907 for game ID 730
Installing breakpad exception handler for appid(steam)/version(1476379980)
[1112/161645:ERROR:ssl_client_socket_openssl.cc(1149)] handshake failed; returned -1, SSL error code 1, net_error -107
[1112/161645:ERROR:ssl_client_socket_openssl.cc(1149)] handshake failed; returned -1, SSL error code 1, net_error -107
[1112/161645:ERROR:ssl_client_socket_openssl.cc(1149)] handshake failed; returned -1, SSL error code 1, net_error -107
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: boadgeojelhgndaghljhdicfkmllpafd
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://boadgeojelhgndaghljhdicfkmllpafd/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: dliochdbjfkdbacpmhlcpmleaejidimm
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://dliochdbjfkdbacpmhlcpmleaejidimm/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: enhhojjnijigcajfphajepfemndkmdlo
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://enhhojjnijigcajfphajepfemndkmdlo/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: fmfcbgogabcbclcofgocippekhfcmgfj
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fmfcbgogabcbclcofgocippekhfcmgfj/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: pkedcjkdefgpdelpbcmbmeomcjbeemfm
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://pkedcjkdefgpdelpbcmbmeomcjbeemfm/cast_sender.js
[1112/161645:WARNING:extension_protocols.cc(430)] Failed to GetPathForExtension: fjhoaacokmgbjemoflkofnenfaiekifl
[1112/161645:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fjhoaacokmgbjemoflkofnenfaiekifl/cast_sender.js
Generating new string page texture 138: 128x256, total string texture memory is 393,22 KB
Generating new string page texture 139: 128x256, total string texture memory is 2,82 MB
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
```


No other driver available.

---

### Post by valereguerin on 2016-11-13
i had a corrupt file in cache ! but after repair it i didn't test again i had installed Beta, works fine. (ubuntu driver: Tahiti)

```
freeman@freeman-sniperone:~$ sudo sysprof
[sudo] password for freeman: 
warning: /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.3800.1 has wrong crc ccd1b775, /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.3800.1 has crc 1083394)
warning: /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0 has wrong crc 19f12a45, /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0 has crc d5c3c1)
warning: /lib/x86_64-linux-gnu/libc-2.23.so has wrong crc 4e01d81e, /lib/x86_64-linux-gnu/libc-2.23.so has crc 46187500)
warning: /usr/lib/debug/lib/x86_64-linux-gnu/libc-2.23.so has wrong crc 7d461875, /lib/x86_64-linux-gnu/libc-2.23.so has crc 46187500)
warning: /usr/lib/x86_64-linux-gnu/libgtk-3.so.0.1800.9 has wrong crc a63cbc43, /usr/lib/x86_64-linux-gnu/libgtk-3.so.0.1800.9 has crc c26898dd)
warning: /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.3800.1 has wrong crc 5cbf3a77, /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.3800.1 has crc 8423ec12)
warning: /usr/lib/x86_64-linux-gnu/libgdk-3.so.0.1800.9 has wrong crc 1eb6144d, /usr/lib/x86_64-linux-gnu/libgdk-3.so.0.1800.9 has crc e37cb509)
warning: /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.3800.1 has wrong crc bc691c3, /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.3800.1 has crc 81152a36)
warning: /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 has wrong crc afbbdc31, /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 has crc a2ee230b)
warning: /lib/x86_64-linux-gnu/libm-2.23.so has wrong crc 8c5bdde3, /lib/x86_64-linux-gnu/libm-2.23.so has crc ae900a31)
warning: /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21 has wrong crc 834c912e, /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21 has crc c67ab13d)
warning: /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0 has wrong crc b483887a, /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0 has crc 38c83e44)
warning: /lib/i386-linux-gnu/libc-2.23.so has wrong crc df83c85a, /lib/i386-linux-gnu/libc-2.23.so has crc 923c8f00)
warning: /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0.2400.30 has wrong crc ed735054, /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0.2400.30 has crc ce943165)
warning: /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.30 has wrong crc 2d78e4e5, /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.30 has crc c5b0258c)
warning: /usr/lib/xorg/modules/input/evdev_drv.so has wrong crc 80decca6, /usr/lib/xorg/modules/input/evdev_drv.so has crc eb65a9f)
warning: /usr/bin/sysprof has wrong crc 19796911, /usr/bin/sysprof has crc 51c1e1a6)
warning: /usr/sbin/preload has wrong crc 26d7f88d, /usr/sbin/preload has crc d6cf28c8)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libfreetype.so.6.8.0 has wrong crc 626af564, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libfreetype.so.6.8.0 has crc b073706d)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3 has wrong crc ca592435, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3 has crc 625b2669)
warning: /usr/lib/x86_64-linux-gnu/libgirepository-1.0.so.1.0.0 has wrong crc 357d2c37, /usr/lib/x86_64-linux-gnu/libgirepository-1.0.so.1.0.0 has crc 4424a28a)
warning: /lib/x86_64-linux-gnu/ld-2.23.so has wrong crc 30b9eb7c, /lib/x86_64-linux-gnu/ld-2.23.so has crc d576ac3f)
warning: /usr/lib/apache2/modules/mod_mpm_event.so has wrong crc e5b3cb62, /usr/lib/apache2/modules/mod_mpm_event.so has crc cf6a3c03)
warning: /lib/x86_64-linux-gnu/libdl-2.23.so has wrong crc 2f5dc0b2, /lib/x86_64-linux-gnu/libdl-2.23.so has crc 18adec9c)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libX11.so.6.3.0 has wrong crc e9a804a1, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libX11.so.6.3.0 has crc 284eea5a)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 has wrong crc cdcbd71a, /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 has crc 21c62f21)
warning: /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0 has wrong crc e9b9988d, /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0 has crc 2077fd66)
warning: /usr/lib/rsyslog/imuxsock.so has wrong crc 2df37baa, /usr/lib/rsyslog/imuxsock.so has crc b051ea1a)
warning: /usr/lib/x86_64-linux-gnu/libgldi.so.3.4.1 has wrong crc 9f8122cb, /usr/lib/x86_64-linux-gnu/libgldi.so.3.4.1 has crc 597c6489)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libglib-2.0.so.0.3200.3 has wrong crc 681ca812, /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libglib-2.0.so.0.3200.3 has crc 5322059b)
warning: /usr/lib/i386-linux-gnu/libstdc++.so.6.0.21 has wrong crc 56675c68, /usr/lib/i386-linux-gnu/libstdc++.so.6.0.21 has crc cdf31522)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1 has wrong crc 128ff2c, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1 has crc 736d5338)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libXext.so.6.4.0 has wrong crc 35d59528, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libXext.so.6.4.0 has crc 3225f09b)
warning: /lib/i386-linux-gnu/libm-2.23.so has wrong crc 12b7ff8c, /lib/i386-linux-gnu/libm-2.23.so has crc 4ced3da1)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libdbus-1.so.3.5.8 has wrong crc d58c5b46, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libdbus-1.so.3.5.8 has crc 734984e7)
warning: /lib/x86_64-linux-gnu/libpcre.so.3.13.2 has wrong crc 276b70fd, /lib/x86_64-linux-gnu/libpcre.so.3.13.2 has crc 22183252)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2 has wrong crc f76109ba, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2 has crc 9b97386d)
warning: /usr/lib/x86_64-linux-gnu/cairo-dock/libcd-system-monitor.so has wrong crc 9620a566, /usr/lib/x86_64-linux-gnu/cairo-dock/libcd-system-monitor.so has crc 9ee57724)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10 has wrong crc 4f85422e, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10 has crc f38cb7dd)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libICE.so.6.3.0 has wrong crc 3df2a549, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libICE.so.6.3.0 has crc 57f8c096)
warning: /usr/sbin/apache2 has wrong crc 4ebc5a99, /usr/sbin/apache2 has crc b37281aa)
warning: /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0 has wrong crc 41b84947, /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0 has crc ceb4ca65)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libSM.so.6.0.1 has wrong crc 17f58aa2, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libSM.so.6.0.1 has crc 244a2e68)
warning: /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so has wrong crc 6fe24d9f, /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so has crc d7d7ff9)
warning: /usr/lib/x86_64-linux-gnu/libnettle.so.6.2 has wrong crc a14a17f5, /usr/lib/x86_64-linux-gnu/libnettle.so.6.2 has crc fa879d1a)
warning: /usr/lib/libclamav.so.7.1.1 has wrong crc be46e962, /usr/lib/libclamav.so.7.1.1 has crc d3f9907)
warning: /usr/bin/freshclam has wrong crc 44e5b842, /usr/bin/freshclam has crc 93420000)
warning: /usr/lib/rtkit/rtkit-daemon has wrong crc 165225e6, /usr/lib/rtkit/rtkit-daemon has crc 9c1154a0)
warning: /usr/lib/x86_64-linux-gnu/cairo-dock/libcd-shortcuts.so has wrong crc 366644b4, /usr/lib/x86_64-linux-gnu/cairo-dock/libcd-shortcuts.so has crc 4d2db430)
warning: /usr/lib/x86_64-linux-gnu/cairo-dock/libcd-AlsaMixer.so has wrong crc 15721e95, /usr/lib/x86_64-linux-gnu/cairo-dock/libcd-AlsaMixer.so has crc a27f7e93)
warning: /lib/x86_64-linux-gnu/libcrypt-2.23.so has wrong crc 30c9d049, /lib/x86_64-linux-gnu/libcrypt-2.23.so has crc 891457b0)
warning: /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.10 has wrong crc 262b3736, /home/freeman/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.10 has crc 48a9ae35)
```


steam error log

```
rm: cannot remove '/home/freeman/.steam/steam': Is a directory
rm: cannot remove '/home/freeman/.steam/bin': Is a directory
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
awk: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"

(steam:17091): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

(steam:17091): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Adwaita/gtk-2.0/gtkrc:1163: error: unexpected identifier `direction', expected character `}'
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Generating new string page texture 7: 128x256, total string texture memory is 131,07 KB
Generating new string page texture 8: 48x256, total string texture memory is 180,22 KB
Generating new string page texture 9: 256x256, total string texture memory is 442,37 KB
Generating new string page texture 10: 64x256, total string texture memory is 507,90 KB
Generating new string page texture 11: 8x256, total string texture memory is 516,10 KB
Generating new string page texture 12: 16x256, total string texture memory is 532,48 KB
Generating new string page texture 13: 24x256, total string texture memory is 557,06 KB
Generating new string page texture 14: 32x256, total string texture memory is 589,82 KB
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
roaming config store loaded successfully - 1273 bytes.
migrating temporary roaming config store
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1478823482)
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/freeman/.steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1478823482)
System startup time: 22,12 seconds
Generating new string page texture 96: 1024x256, total string texture memory is 1,64 MB
Generating new string page texture 97: 256x256, total string texture memory is 262,14 KB
Generating new string page texture 99: 384x256, total string texture memory is 2,03 MB
bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by bash)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
rm: cannot remove '/home/freeman/.steam/bin': Is a directory
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
awk: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
/usr/bin/ldd: line 119: printf: write error: Broken pipe
ExecCommandLine: "/home/freeman/.steam/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 102: 128x256, total string texture memory is 2,16 MB
Generating new string page texture 103: 256x256, total string texture memory is 2,42 MB
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Setting breakpad minidump AppID = 769
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded no]
[1114/005136:ERROR:web_plugin_impl.cc(38)] Widevine registration is not supported after context initialization
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Generating new string page texture 115: 128x256, total string texture memory is 393,22 KB
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
rm: cannot remove '/home/freeman/.steam/steam': Is a directory
rm: cannot remove '/home/freeman/.steam/bin': Is a directory
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
awk: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
/usr/bin/ldd: line 119: printf: write error: Broken pipe
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"

(steam:25122): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

(steam:25122): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Adwaita/gtk-2.0/gtkrc:1163: error: unexpected identifier `direction', expected character `}'
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1478823482)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Generating new string page texture 2: 48x256, total string texture memory is 49,15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311,30 KB
roaming config store loaded successfully - 1273 bytes.
migrating temporary roaming config store
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/freeman/.steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1478823482)
System startup time: 2,08 seconds
bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by bash)
Generating new string page texture 85: 1024x256, total string texture memory is 1,36 MB
Generating new string page texture 86: 128x256, total string texture memory is 1,49 MB
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Generating new string page texture 87: 256x256, total string texture memory is 262,14 KB
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Generating new string page texture 88: 32x256, total string texture memory is 1,52 MB
rm: cannot remove '/home/freeman/.steam/bin': Is a directory
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
Installing breakpad exception handler for appid(steam)/version(1478823482)
awk: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Installing breakpad exception handler for appid(steam)/version(1478823482)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Generating new string page texture 90: 384x256, total string texture memory is 1,92 MB
/usr/bin/ldd: line 119: printf: write error: Broken pipe
ExecCommandLine: "/home/freeman/.steam/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 92: 16x256, total string texture memory is 1,93 MB
Game update: AppID 730 "Counter-Strike: Global Offensive", ProcID 25694, IP 0.0.0.0:0
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 25694 for game ID 730
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
pid 25697 != 25696, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Generating new string page texture 97: 64x256, total string texture memory is 2,00 MB
>>> Adding process 25695 for game ID 730
>>> Adding process 25696 for game ID 730
>>> Adding process 25698 for game ID 730
>>> Adding process 25699 for game ID 730
Installing breakpad exception handler for appid(gameoverlayui)/version(20161110233134)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Using breakpad crash handler
Setting breakpad minidump AppID = 730
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
No cached sticky mapping in GetActionSetHandle. Native Steam Controller support won't work.
Installing breakpad exception handler for appid(steam)/version(1478823482)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 26306 for game ID 730
>>> Adding process 26307 for game ID 730
[1114/014110:ERROR:ssl_client_socket_impl.cc(1146)] handshake failed; returned -1, SSL error code 1, net_error -107
[1114/014110:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: pkedcjkdefgpdelpbcmbmeomcjbeemfm
[1114/014110:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://pkedcjkdefgpdelpbcmbmeomcjbeemfm/cast_sender.js
[1114/014110:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: fjhoaacokmgbjemoflkofnenfaiekifl
[1114/014110:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fjhoaacokmgbjemoflkofnenfaiekifl/cast_sender.js
[1114/014110:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: boadgeojelhgndaghljhdicfkmllpafd
[1114/014110:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://boadgeojelhgndaghljhdicfkmllpafd/cast_sender.js
[1114/014110:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: dliochdbjfkdbacpmhlcpmleaejidimm
[1114/014110:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://dliochdbjfkdbacpmhlcpmleaejidimm/cast_sender.js
[1114/014110:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: enhhojjnijigcajfphajepfemndkmdlo
[1114/014110:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://enhhojjnijigcajfphajepfemndkmdlo/cast_sender.js
[1114/014110:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: fmfcbgogabcbclcofgocippekhfcmgfj
[1114/014110:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fmfcbgogabcbclcofgocippekhfcmgfj/cast_sender.js
[1114/014310:ERROR:ssl_client_socket_impl.cc(1146)] handshake failed; returned -1, SSL error code 1, net_error -107
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Setting breakpad minidump AppID = 769
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded no]
[1114/014504:ERROR:web_plugin_impl.cc(38)] Widevine registration is not supported after context initialization
[1114/014538:ERROR:ssl_client_socket_impl.cc(1146)] handshake failed; returned -1, SSL error code 1, net_error -107
[1114/014538:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: pkedcjkdefgpdelpbcmbmeomcjbeemfm
[1114/014538:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://pkedcjkdefgpdelpbcmbmeomcjbeemfm/cast_sender.js
[1114/014538:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: fjhoaacokmgbjemoflkofnenfaiekifl
[1114/014538:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fjhoaacokmgbjemoflkofnenfaiekifl/cast_sender.js
[1114/014538:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: boadgeojelhgndaghljhdicfkmllpafd
[1114/014538:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://boadgeojelhgndaghljhdicfkmllpafd/cast_sender.js
[1114/014538:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: dliochdbjfkdbacpmhlcpmleaejidimm
[1114/014538:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://dliochdbjfkdbacpmhlcpmleaejidimm/cast_sender.js
[1114/014538:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: enhhojjnijigcajfphajepfemndkmdlo
[1114/014538:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://enhhojjnijigcajfphajepfemndkmdlo/cast_sender.js
[1114/014538:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: fmfcbgogabcbclcofgocippekhfcmgfj
[1114/014538:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fmfcbgogabcbclcofgocippekhfcmgfj/cast_sender.js
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
[1114/014754:ERROR:ssl_client_socket_impl.cc(1146)] handshake failed; returned -1, SSL error code 1, net_error -107
[1114/014754:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: pkedcjkdefgpdelpbcmbmeomcjbeemfm
[1114/014754:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://pkedcjkdefgpdelpbcmbmeomcjbeemfm/cast_sender.js
[1114/014754:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: fjhoaacokmgbjemoflkofnenfaiekifl
[1114/014754:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fjhoaacokmgbjemoflkofnenfaiekifl/cast_sender.js
[1114/014754:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: boadgeojelhgndaghljhdicfkmllpafd
[1114/014754:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://boadgeojelhgndaghljhdicfkmllpafd/cast_sender.js
[1114/014754:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: dliochdbjfkdbacpmhlcpmleaejidimm
[1114/014754:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://dliochdbjfkdbacpmhlcpmleaejidimm/cast_sender.js
[1114/014754:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: enhhojjnijigcajfphajepfemndkmdlo
[1114/014754:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://enhhojjnijigcajfphajepfemndkmdlo/cast_sender.js
[1114/014754:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: fmfcbgogabcbclcofgocippekhfcmgfj
[1114/014754:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fmfcbgogabcbclcofgocippekhfcmgfj/cast_sender.js
Game removed: AppID 730 "Counter-Strike: Global Offensive", ProcID 25699 
No cached sticky mapping in ActivateActionSet.Generating new string page texture 100: 128x256, total string texture memory is 393,22 KB
Generating new string page texture 102: 24x256, total string texture memory is 2,02 MB
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
rm: cannot remove '/home/freeman/.steam/steam': Is a directory
rm: cannot remove '/home/freeman/.steam/bin': Is a directory
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
/usr/bin/ldd: line 119: printf: write error: Broken pipe
awk: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"

(steam:27361): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

(steam:27361): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Adwaita/gtk-2.0/gtkrc:1163: error: unexpected identifier `direction', expected character `}'
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1478823482)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Generating new string page texture 7: 128x256, total string texture memory is 131,07 KB
Generating new string page texture 8: 48x256, total string texture memory is 180,22 KB
Generating new string page texture 9: 256x256, total string texture memory is 442,37 KB
Generating new string page texture 10: 64x256, total string texture memory is 507,90 KB
Generating new string page texture 11: 8x256, total string texture memory is 516,10 KB
Generating new string page texture 12: 16x256, total string texture memory is 532,48 KB
Generating new string page texture 13: 24x256, total string texture memory is 557,06 KB
Generating new string page texture 14: 32x256, total string texture memory is 589,82 KB
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/freeman/.steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1478823482)
System startup time: 10,88 seconds
Generating new string page texture 96: 1024x256, total string texture memory is 1,64 MB
Generating new string page texture 97: 256x256, total string texture memory is 262,14 KB
bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by bash)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Generating new string page texture 100: 384x256, total string texture memory is 2,03 MB
rm: cannot remove '/home/freeman/.steam/bin': Is a directory
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
awk: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /lib/x86_64-linux-gnu/libreadline.so.6)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
/usr/bin/ldd: line 119: printf: write error: Broken pipe
ExecCommandLine: "/home/freeman/.steam/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
roaming config store loaded successfully - 1273 bytes.
migrating temporary roaming config store
Generating new string page texture 104: 128x256, total string texture memory is 2,16 MB
Generating new string page texture 105: 256x256, total string texture memory is 2,42 MB
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
Game update: AppID 730 "Counter-Strike: Global Offensive", ProcID 29740, IP 0.0.0.0:0
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 29740 for game ID 730
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
pid 29743 != 29742, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 29741 for game ID 730
>>> Adding process 29742 for game ID 730
>>> Adding process 29744 for game ID 730
>>> Adding process 29745 for game ID 730
Installing breakpad exception handler for appid(gameoverlayui)/version(20161110233134)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Using breakpad crash handler
Setting breakpad minidump AppID = 730
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
No cached sticky mapping in GetActionSetHandle. Native Steam Controller support won't work.
/home/freeman/.steam/steam/steamapps/common/Counter-Strike Global Offensive/csgo.sh: line 64: 29745 Killed                  ${DEBUGGER} "${GAMEROOT}"/${GAMEEXE} "$@"
Game removed: AppID 730 "Counter-Strike: Global Offensive", ProcID 29745 
No cached sticky mapping in ActivateActionSet.Generating new string page texture 118: 256x256, total string texture memory is 2,69 MB
Generating new string page texture 119: 128x256, total string texture memory is 393,22 KB
Game update: AppID 730 "Counter-Strike: Global Offensive", ProcID 31753, IP 0.0.0.0:0
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 31753 for game ID 730
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
/bin/bash: /home/freeman/.steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
pid 31756 != 31755, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 31754 for game ID 730
>>> Adding process 31755 for game ID 730
>>> Adding process 31757 for game ID 730
>>> Adding process 31758 for game ID 730
Installing breakpad exception handler for appid(gameoverlayui)/version(20161110233134)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Using breakpad crash handler
Setting breakpad minidump AppID = 730
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
Installing breakpad exception handler for appid(steam)/version(1478823482)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/freeman/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
>>> Adding process 32550 for game ID 730
>>> Adding process 32551 for game ID 730
Installing breakpad exception handler for appid(steam)/version(1478823482)
Installing breakpad exception handler for appid(steam)/version(1478823482)
[1114/015312:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: pkedcjkdefgpdelpbcmbmeomcjbeemfm
[1114/015312:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://pkedcjkdefgpdelpbcmbmeomcjbeemfm/cast_sender.js
[1114/015312:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: fjhoaacokmgbjemoflkofnenfaiekifl
[1114/015312:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fjhoaacokmgbjemoflkofnenfaiekifl/cast_sender.js
[1114/015312:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: boadgeojelhgndaghljhdicfkmllpafd
[1114/015312:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://boadgeojelhgndaghljhdicfkmllpafd/cast_sender.js
[1114/015312:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: dliochdbjfkdbacpmhlcpmleaejidimm
[1114/015312:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://dliochdbjfkdbacpmhlcpmleaejidimm/cast_sender.js
[1114/015312:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: enhhojjnijigcajfphajepfemndkmdlo
[1114/015312:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://enhhojjnijigcajfphajepfemndkmdlo/cast_sender.js
[1114/015312:WARNING:extension_protocols.cc(445)] Failed to GetPathForExtension: fmfcbgogabcbclcofgocippekhfcmgfj
[1114/015312:WARNING:url_request_job_manager.cc(89)] Failed to map: chrome-extension://fmfcbgogabcbclcofgocippekhfcmgfj/cast_sender.js
Setting breakpad minidump AppID = 769
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded no]
[1114/015316:ERROR:web_plugin_impl.cc(38)] Widevine registration is not supported after context initialization
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198052678839 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198052678839
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
```

```
Nov 14 02:56:15 freeman-sniperone gnome-session[4304]:  failed to dlopen /home/freeman/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/studiorender_client.so error=/home/freeman/.ste
Nov 14 02:56:15 freeman-sniperone gnome-session[4304]: ** (soffice:27227): WARNING **: Unknown event notification 36
Nov 14 02:58:54 freeman-sniperone crash_20161114025854_4.dmp[17100]: Uploading dump (out-of-process)#012/tmp/dumps/crash_20161114025854_4.dmp
Nov 14 02:58:56 freeman-sniperone assert_20161114025856_2.dmp[17728]: Uploading dump (out-of-process)#012/tmp/dumps/assert_20161114025856_2.dmp
Nov 14 02:59:01 freeman-sniperone crash_20161114025854_4.dmp[17100]: Finished uploading minidump (out-of-process): success = yes
Nov 14 02:59:01 freeman-sniperone crash_20161114025854_4.dmp[17100]: response: Discarded=1
Nov 14 02:59:01 freeman-sniperone crash_20161114025854_4.dmp[17100]: file ''/tmp/dumps/crash_20161114025854_4.dmp'', upload yes: ''Discarded=1''
Nov 14 02:59:06 freeman-sniperone assert_20161114025856_2.dmp[17728]: Finished uploading minidump (out-of-process): success = yes
Nov 14 02:59:06 freeman-sniperone assert_20161114025856_2.dmp[17728]: response: Discarded=1
Nov 14 02:59:06 freeman-sniperone assert_20161114025856_2.dmp[17728]: file ''/tmp/dumps/assert_20161114025856_2.dmp'', upload yes: ''Discarded=1''
Nov 14 03:00:54 freeman-sniperone gnome-session[4304]: Promise rejected after context unloaded
Nov 14 03:01:00 freeman-sniperone gnome-session[4304]: message repeated 3 times: [ Promise rejected after context unloaded]
Nov 14 03:03:11 freeman-sniperone crash_20161114030311_2.dmp[25406]: Uploading dump (out-of-process)#012/tmp/dumps/crash_20161114030311_2.dmp
Nov 14 03:03:12 freeman-sniperone assert_20161114025511_1.dmp[25431]: Uploading dump (out-of-process)#012/tmp/dumps/assert_20161114025511_1.dmp
Nov 14 03:03:12 freeman-sniperone kernel: [ 1459.333298] show_signal_msg: 174 callbacks suppressed
Nov 14 03:03:12 freeman-sniperone kernel: [ 1459.333301] HTMLController [10003]: segfault at 58 ip 00000000ec58db13 sp 00000000ec47bf20 error 4 in chromehtml.so[ec57d000+14e000]
Nov 14 03:03:12 freeman-sniperone gnome-session[4304]: Forced create but already created for SharedObjectEvent
Nov 14 03:03:15 freeman-sniperone crash_20161114030311_2.dmp[25406]: Finished uploading minidump (out-of-process): success = yes
Nov 14 03:03:15 freeman-sniperone crash_20161114030311_2.dmp[25406]: response: Discarded=1
Nov 14 03:03:15 freeman-sniperone crash_20161114030311_2.dmp[25406]: file ''/tmp/dumps/crash_20161114030311_2.dmp'', upload yes: ''Discarded=1''
Nov 14 03:03:15 freeman-sniperone assert_20161114025511_1.dmp[25431]: Finished uploading minidump (out-of-process): success = yes
Nov 14 03:03:15 freeman-sniperone assert_20161114025511_1.dmp[25431]: response: CrashID=bp-9149eec3-740b-4a7d-8de6-558442161113
Nov 14 03:03:15 freeman-sniperone assert_20161114025511_1.dmp[25431]: file ''/tmp/dumps/assert_20161114025511_1.dmp'', upload yes: ''CrashID=bp-9149eec3-740b-4a7d-8de6-558442161113''
Nov 14 03:09:01 freeman-sniperone CRON[4821]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 14 03:16:13 freeman-sniperone gnome-session[4304]: Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Nov 14 03:16:13 freeman-sniperone gnome-session[4304]: Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2400004 (.steam - G)
Nov 14 03:16:29 freeman-sniperone gnome-session[4304]: (soffice:19101): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
Nov 14 03:16:29 freeman-sniperone gnome-session[4304]: (soffice:19101): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
Nov 14 03:16:29 freeman-sniperone systemd[1]: Started CUPS Scheduler.
Nov 14 03:17:01 freeman-sniperone CRON[20398]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 14 03:20:23 freeman-sniperone dbus[1422]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Nov 14 03:20:23 freeman-sniperone systemd[1]: Starting Hostname Service...
Nov 14 03:20:23 freeman-sniperone dbus[1422]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov 14 03:20:23 freeman-sniperone systemd[1]: Started Hostname Service.
Nov 14 03:20:23 freeman-sniperone org.gtk.vfs.Daemon[4141]: ** (process:5840): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/3 (g-dbus-error-quark, 19)
Nov 14 03:20:23 freeman-sniperone org.gtk.vfs.Daemon[4141]: ** (process:26436): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend



```

---

