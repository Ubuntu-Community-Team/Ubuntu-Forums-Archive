---
title: "Cant start up Nexuiz / nVidia Legacy"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by Quibly on 2007-03-19
Ok I just installed Nexuiz using the guide that I found in the forums. Before this I had my nVidia legacy driver installed with easyubuntu. I went to the terminal and wrote nexuiz and this is what I got:
```

[: 24: ==: unexpected operator
^7Nexuiz Linux 02:33:28 Jul  5 2006
^7Trying to load library... "libz.so.1" - loaded.
^7Compressed files support enabled
^7Added packfile data/data20060614.pk3 (2849 files)
^7Added packfile data/data20060616_hotfix.pk3 (3 files)
^7Added packfile data/music20060614.pk3 (9 files)
^7Console initialized.
^7Playing registered version.
^7Trying to load library... "libcurl.so.3" - loaded.
^7cURL support enabled
^7Initializing client
^7Trying to load library... "libvorbis.so.0" - loaded.
^7Trying to load library... "libvorbisfile.so.3" - loaded.
^7Ogg Vorbis support enabled
^7couldn't exec config.cfg
^7couldn't exec autoexec.cfg
^7Starting video system
^7Video: fullscreen 800x600x32x60hz
^7Linked against SDL version 1.2.9
^7Using SDL library version 1.2.10
^7Failed to set video mode to 800x600: <%d]8#h0#
*** glibc detected *** ./nexuiz-sdl: corrupted double-linked list: 0xb7ea4158 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7dd7c5a]
/lib/tls/i686/cmov/libc.so.6[0xb7dd9ecd]
/lib/tls/i686/cmov/libc.so.6(malloc+0x7f)[0xb7ddb83f]
/usr/lib/libX11.so.6[0xb778ef04]
/usr/lib/libX11.so.6(XrmGetFileDatabase+0x24)[0xb7790a34]
/usr/lib/libX11.so.6(XGetErrorDatabaseText+0x1f5)[0xb7765945]
/usr/lib/libX11.so.6(XGetErrorText+0x1c2)[0xb7765b92]
/usr/lib/libX11.so.6(_XDefaultError+0x6b)[0xb778856b]
/usr/lib/libSDL-1.2.so.0[0xb7efb356]
/usr/lib/libX11.so.6(_XError+0x12a)[0xb7788dfa]
/usr/lib/libX11.so.6(_XReply+0x184)[0xb778a9e4]
/usr/lib/libX11.so.6(XGetScreenSaver+0x6a)[0xb776c27a]
/usr/lib/libSDL-1.2.so.0[0xb7ef2aea]
/usr/lib/libSDL-1.2.so.0[0xb7ef58bb]
/usr/lib/libSDL-1.2.so.0[0xb7efbb80]
/usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x50)[0xb7eeb6b0]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x65)[0xb7ebfe35]
/usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1e)[0xb7ebfeae]
/usr/lib/libSDL-1.2.so.0[0xb7ec06ef]
[0xffffe420]
/usr/lib/libSDL-1.2.so.0[0xb7ef244e]
/usr/lib/libSDL-1.2.so.0[0xb7efbbbc]
/usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x50)[0xb7eeb6b0]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x65)[0xb7ebfe35]
./nexuiz-sdl[0x804a2c3]
./nexuiz-sdl[0x804a5c7]
./nexuiz-sdl[0x8166a23]
./nexuiz-sdl[0x8166caa]
./nexuiz-sdl[0x80c075d]
./nexuiz-sdl[0x807a614]
./nexuiz-sdl[0x80c0d57]
./nexuiz-sdl[0x80c1093]
./nexuiz-sdl[0x804a041]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7d888cc]
./nexuiz-sdl[0x8049c31]
======= Memory map: ========
08048000-081a1000 r-xp 00000000 03:01 2153356    /usr/lib/games/nexuiz/nexuiz-sdl
081a1000-081b4000 rw-p 00159000 03:01 2153356    /usr/lib/games/nexuiz/nexuiz-sdl
081b4000-0ad4c000 rw-p 081b4000 00:00 0          [heap]
b693e000-b69d6000 rw-p b693e000 00:00 0 
b69d6000-b70f7000 r-xp 00000000 03:01 2020795    /usr/lib/libGLcore.so.1.0.7184
b70f7000-b7113000 rw-p 00720000 03:01 2020795    /usr/lib/libGLcore.so.1.0.7184
b7113000-b7127000 rw-p b7113000 00:00 0 
b7127000-b7188000 r-xp 00000000 03:01 2020766    /usr/lib/libGL.so.1.0.7184
b7188000-b719f000 rwxp 00060000 03:01 2020766    /usr/lib/libGL.so.1.0.7184
b719f000-b71a0000 rwxp b719f000 00:00 0 
b7500000-b7521000 rw-p b7500000 00:00 0 
b7521000-b7600000 ---p b7521000 00:00 0 
b7695000-b769f000 r-xp 00000000 03:01 2314676    /lib/libgcc_s.so.1
b769f000-b76a0000 rw-p 00009000 03:01 2314676    /lib/libgcc_s.so.1
b76ab000-b76cc000 rw-p b76ab000 00:00 0 
b76cc000-b76d2000 r-xp 00000000 03:01 1417177    /usr/lib/libvorbisfile.so.3.1.1
b76d2000-b76d3000 rw-p 00005000 03:01 1417177    /usr/lib/libvorbisfile.so.3.1.1
b76d3000-b76d7000 r-xp 00000000 03:01 2021661    /usr/lib/libogg.so.0.5.3
b76d7000-b76d8000 rw-p 00003000 03:01 2021661    /usr/lib/libogg.so.0.5.3
b76d8000-b76f1000 r-xp 00000000 03:01 2021192    /usr/lib/libvorbis.so.0.3.1
b76f1000-b76ff000 rw-p 00019000 03:01 2021192    /usr/lib/libvorbis.so.0.3.1
b76ff000-b7707000 r-xp 00000000 03:01 2020832    /usr/lib/libXcursor.so.1.0.2
b7707000-b7708000 rw-p 00007000 03:01 2020832    /usr/lib/libXcursor.so.1.0.2
b770f000-b7711000 rwxp 00000000 00:0c 1385       /dev/zero
b7711000-b7712000 r-xp 00000000 03:01 2118199    /usr/lib/tls/libnvidia-tls.so.1.0.7184
b7712000-b7713000 rw-p 00000000 03:01 2118199    /usr/lib/tls/libnvidia-tls.so.1.0.7184
b7713000-b772f000 r-xp 00000000 03:01 2134712    /usr/lib/X11/locale/common/ximcp.so.2.0.0
b772f000-b7731000 rw-p 0001b000 03:01 2134712    /usr/lib/X11/locale/common/ximcp.so.2.0.0
b7731000-b7733000 r-xp 00000000 03:01 2020803    /usr/lib/libXrandr.so.2.0.0
b7733000-b7734000 rw-p 00002000 03:01 2020803    /usr/lib/libXrandr.so.2.0.0
b7734000-b773b000 r-xp 00000000 03:01 2020643    /usr/lib/libXrender.so.1.3.0
b773b000-b773c000 rw-p 00006000 03:01 2020643    /usr/lib/libXrender.so.1.3.0
b773c000-b7748000 r-xp 00000000 03:01 2020566    /usr/lib/libXext.so.6.4.0
b7748000-b7749000 rw-p 0000c000 03:01 2020566    /usr/lib/libXext.so.6.4.0
b7749000-b774d000 r-xp 00000000 03:01 2020700    /usr/lib/libXdmcp.so.6.0.0
b774d000-b774e000 rw-p 00003000 03:01 2020700    /usr/lib/libXdmcp.so.6.0.0
b774e000-b7814000 r-xp 00000000 03:01 2020570    /usr/lib/libX11.so.6.2.0
b7814000-b7817000 rw-p 000c5000 03:01 2020570    /usr/lib/libX11.so.6.2.0
b7817000-b791a000 rw-p b7817000 00:00 0 
b791a000-b7a3c000 r-xp 00000000 03:01 2068863    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7a3c000-b7a51000 rw-p 00121000 03:01 2068863    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7a51000-b7a54000 rw-p b7a51000 00:00 0 
b7a54000-b7a8f000 r-xp 00000000 03:01 2068901    /usr/lib/i686/cmov/libssl.so.0.9.8
b7a8f000-b7a93000 rw-p 0003b000 03:01 2068901    /usr/lib/i686/cmov/libssl.so.0.9.8
b7a93000-b7ac2000 r-xp 00000000 03:01 2020899    /usr/lib/libidn.so.11.5.17
b7ac2000-b7ac3000 rw-p 0002e000 03:01 2020899    /usr/lib/libidn.so.11.5.17
b7ac3000-b7ad2000 r-xp 00000000 03:01 2345646    /lib/tls/i686/cmov/libresolv-2.4.so
b7ad2000-b7ad4000 rw-p 0000f000 03:01 2345646    /lib/tls/i686/cmov/libresolv-2.4.so
b7ad4000-b7ad6000 rw-p b7ad4000 00:00 0 
b7ad6000-b7afa000 r-xp 00000000 03:01 2021585    /usr/lib/libk5crypto.so.3.0
b7afa000-b7afb000 rw-p 00023000 03:01 2021585    /usr/lib/libk5crypto.so.3.0
b7afb000-b7b75000 r-xp 00000000 03:01 2021587    /usr/lib/libkrb5.so.3.2
b7b75000-b7b77000 rw-p 0007a000 03:01 2021587    /usr/lib/libkrb5.so.3.2
b7b77000-b7b92000 r-xp 00000000 03:01 2020053    /usr/lib/libgssapi_krb5.so.2.2
b7b92000-b7b93000 rw-p 0001b000 03:01 2020053    /usr/lib/libgssapi_krb5.so.2.2
b7b93000-b7bc6000 r-xp 00000000 03:01 2021400    /usr/lib/libcurl.so.3.0.0
b7bc6000-b7bc7000 rw-p 00032000 03:01 2021400    /usr/lib/libcurl.so.3.0.0
b7bc7000-b7bcb000 r-xp 00000000 03:01 2020755    /usr/lib/libXfixes.so.3.1.0
b7bcb000-b7bcc000 rw-p 00003000 03:01 2020755    /usr/lib/libXfixes.so.3.1.0
b7bcc000-b7bd1000 r-xp 00000000 03:01 2134715    /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b7bd1000-b7bd2000 rw-p 00004000 03:01 2134715    /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b7bd2000-b7c46000 rw-p b7bd2000 00:00 0 
b7c46000-b7c59000 r-xp 00000000 03:01 2020664    /usr/lib/libz.so.1.2.3
b7c59000-b7c5a000 rw-p 00012000 03:01 2020664    /usr/lib/libz.so.1.2.3
b7c5a000-b7c66000 r-xp 00000000 03:01 2021491    /usr/lib/libdirect-0.9.so.24.0.0
b7c66000-b7c67000 rw-p 0000c000 03:01 2021491    /usr/lib/libdirect-0.9.so.24.0.0
b7c67000-b7c6b000 r-xp 00000000 03:01 2021655    /usr/lib/libfusion-0.9.so.24.0.0
b7c6b000-b7c6c000 rw-p 00003000 03:01 2021655    /usr/lib/libfusion-0.9.so.24.0.0
b7c6c000-b7cb8000 r-xp 00000000 03:01 2021532    /usr/lib/libdirectfb-0.9.so.24.0.0
b7cb8000-b7cba000 rw-p 0004b000 03:01 2021532    /usr/lib/libdirectfb-0.9.so.24.0.0
b7cba000-b7cbb000 rw-p b7cba000 00:00 0 
b7cbb000-b7d6e000 r-xp 00000000 03:01 2020063    /usr/lib/libasound.so.2.0.0
b7d6e000-b7d73000 rw-p 000b2000 03:01 2020063    /usr/lib/libasound.so.2.0.0
b7d73000-b7ea0000 r-xp 00000000 03:01 2345596    /lib/tls/i686/cmov/libc-2.4.so
b7ea0000-b7ea2000 r--p 0012c000 03:01 2345596    /lib/tls/i686/cmov/libc-2.4.so
b7ea2000-b7ea4000 rw-p 0012e000 03:01 2345596    /lib/tls/i686/cmov/libc-2.4.so
b7ea4000-b7ea7000 rw-p b7ea4000 00:00 0 
b7ea7000-b7eb6000 r-xp 00000000 03:01 2345645    /lib/tls/i686/cmov/libpthread-2.4.so
b7eb6000-b7eb8000 rw-p 0000f000 03:01 2345645    /lib/tls/i686/cmov/libpthread-2.4.so
b7eb8000-b7eba000 rw-p b7eb8000 00:00 0 
b7eba000-b7f1e000 r-xp 00000000 03:01 2021905    /usr/lib/libSDL-1.2.so.0.7.3
b7f1e000-b7f20000 rw-p 00064000 03:01 2021905    /usr/lib/libSDL-1.2.so.0.7.3
b7f20000-b7f48000 rw-p b7f20000 00:00 0 
b7f48000-b7f4a000 r-xp 00000000 03:01 2345602    /lib/tls/i686/cmov/libdl-2.4.so
b7f4a000-b7f4c000 rw-p 00001000 03:01 2345602    /lib/tls/i686/cmov/libdl-2.4.so
b7f4c000-b7f70000 r-xp 00000000 03:01 2345603    /lib/tls/i686/cmov/libm-2.4.so
b7f70000-b7f72000 rw-p 00023000 03:01 2345603    /lib/tls/i686/cmov/libm-2.4.so
b7f72000-b7f73000 rw-p b7f72000 00:00 0 
b7f73000-b7f75000 r-xp 00000000 03:01 2020075    /usr/lib/libXau.so.6.0.0
b7f75000-b7f76000 rw-p 00001000 03:01 2020075    /usr/lib/libXau.so.6.0.0
b7f76000-b7f78000 r-xp 00000000 03:01 2312923    /lib/libcom_err.so.2.1
b7f78000-b7f79000 rw-p 00001000 03:01 2312923    /lib/libcom_err.so.2.1
b7f79000-b7f7d000 r-xp 00000000 03:01 2021588    /usr/lib/libkrb5support.so.0.0
b7f7d000-b7f7e000 rw-p 00003000 03:01 2021588    /usr/lib/libkrb5support.so.0.0
b7f7e000-b7f7f000 rw-p b7f7e000 00:00 0 
b7f7f000-b7f98000 r-xp 00000000 03:01 2312918    /lib/ld-2.4.so
b7f98000-b7f9a000 rw-p 00018000 03:01 2312918    /lib/ld-2.4.so
bf8fa000-bf90f000 rwxp bf8fa000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted

```
While the terminal wrote this a windows opened with a black background for a second and then closed. So I went to the wiki and installed the nVidia legacy driver again. And then I tried opening nexuiz again and got the same problem....

I have an old pc with a PIII 1.2ghz processor, 256 mb ram...

Thanks for any help-
:)

---

### Post by Quibly on 2007-03-20
Bump

---

