---
title: "mupen64plus crash: Majoras Mask, Hi-res textures"
date: 2009-07-28
forum: Gaming &amp; Leisure
---

### Post by grossaffe on 2009-07-28
I've been trying to play Majora's Mask on Mupen64plus with Rice's graphics plugin 1.5 using Hi-res textures (dipji's realistic textures pack), but it crashes just as it starts to enter the playable part of the game (you can load your game, and it'll go to the intro thing that tells you how much time you have left, but once its about to take you into gameplay it crashes).

Here's the console output I get when it crashes (I included the last texture it loaded as well in case that may be the cause of the crash).  Has anyone else had a similar problem and does anyone know of a solution (other than to just not use those textures for the game)?
```
Loaded hi-res texture: /home/christian/.mupen64plus/hires_texture/ZELDA MAJORA'S MASK/005-Lune/ZELDA MAJORA'S MASK#1E6DE584#2#0#1B72EA64_ciByRGBA.png
*** glibc detected *** mupen64plus: munmap_chunk(): invalid pointer: 0x00007f460fa88900 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x7f46265acd46]
/usr/local/share/mupen64plus/plugins/ricevideo.so(_Z16LoadHiresTextureR14TxtrCacheEntry+0x52d)[0x7f46220b3d5d]
/usr/local/share/mupen64plus/plugins/ricevideo.so(_Z15PrepareTexturesv+0x44f)[0x7f46220c93ef]
/usr/local/share/mupen64plus/plugins/ricevideo.so(_Z13RSP_GBI2_Tri2P3Gfx+0x1ee)[0x7f46220cb70e]
/usr/local/share/mupen64plus/plugins/ricevideo.so(_Z16DLParser_ProcessP6OSTask+0x1fb)[0x7f46220c7e9b]
/usr/local/share/mupen64plus/plugins/ricevideo.so(_Z17ProcessDListStep2v+0x4b)[0x7f46220a507b]
/usr/local/share/mupen64plus/plugins/mupen64_hle_rsp_azimer.so(DoRspCycles+0x338)[0x7f4621e4da18]
mupen64plus(update_SP+0x355)[0x4572c5]
[0x7f4618d368e1]
======= Memory map: ========
00400000-004d7000 r-xp 00000000 08:05 3883352                            /usr/local/bin/mupen64plus
006d6000-006d7000 r-xp 000d6000 08:05 3883352                            /usr/local/bin/mupen64plus
006d7000-006db000 rwxp 000d7000 08:05 3883352                            /usr/local/bin/mupen64plus
006db000-03013000 rwxp 006db000 00:00 0                                  [heap]
4087a000-408ff000 rwxp 00000000 00:0e 1029                               /dev/zero
40fcc000-40fce000 rwxp 00000000 00:0e 1029                               /dev/zero
40fce000-40fcf000 ---p 40fce000 00:00 0 
40fcf000-417cf000 rwxp 40fcf000 00:00 0 
417cf000-417d0000 ---p 417cf000 00:00 0 
417d0000-41fd0000 rwxp 417d0000 00:00 0 
41fd0000-41fd1000 ---p 41fd0000 00:00 0 
41fd1000-427d1000 rwxp 41fd1000 00:00 0 
427d1000-427d2000 ---p 427d1000 00:00 0 
427d2000-42fd2000 rwxp 427d2000 00:00 0 
7f4608000000-7f460bff5000 rwxp 7f4608000000 00:00 0 
7f460bff5000-7f460c000000 ---p 7f460bff5000 00:00 0 
7f460c000000-7f460fb09000 rwxp 7f460c000000 00:00 0 
7f460fb09000-7f4610000000 ---p 7f460fb09000 00:00 0 
7f4610000000-7f4613fc0000 rwxp 7f4610000000 00:00 0 
7f4613fc0000-7f4614000000 ---p 7f4613fc0000 00:00 0 
7f4615f7f000-7f4615fff000 rwxs 43518000 00:0e 13913                      /dev/nvidia0
7f4615fff000-7f461bff8000 rwxp 7f4615fff000 00:00 0 
7f461bff8000-7f461c000000 ---p 7f461bff8000 00:00 0 
7f461c277000-7f461c288000 r-xp 00000000 08:05 4112856                    /usr/local/share/mupen64plus/fonts/font.ttf
7f461c298000-7f461c2b8000 rwxs 00000000 00:09 48627725                   /SYSV0056a4d6 (deleted)
7f461c2b8000-7f461c4b8000 rwxs 509af000 00:0e 13913                      /dev/nvidia0
7f461c4b8000-7f461c5b8000 rwxs 4287b000 00:0e 13913                      /dev/nvidia0
7f461c5b8000-7f461c5b9000 rwxs fdc06000 00:0e 13913                      /dev/nvidia0
7f461c5b9000-7f461c5f9000 rwxs 341aa000 00:0e 13913                      /dev/nvidia0
7f461c609000-7f461c619000 rwxs 00000000 00:0e 12734                      /dev/snd/pcmC0D0p
7f461c619000-7f461c63b000 rwxs 00000000 00:09 65536                      /SYSV00000000 (deleted)
7f461c63b000-7f461c654000 r-xp 00000000 08:05 3472                       /lib/libselinux.so.1
7f461c654000-7f461c854000 ---p 00019000 08:05 3472                       /lib/libselinux.so.1
7f461c854000-7f461c856000 rwxp 00019000 08:05 3472                       /lib/libselinux.so.1
7f461c856000-7f461c857000 rwxp 7f461c856000 00:00 0 
7f461c857000-7f461c866000 r-xp 00000000 08:05 3412                       /lib/libbz2.so.1.0.4
7f461c866000-7f461ca65000 ---p 0000f000 08:05 3412                       /lib/libbz2.so.1.0.4
7f461ca65000-7f461ca67000 rwxp 0000e000 08:05 3412                       /lib/libbz2.so.1.0.4
7f461ca67000-7f461cad5000 r-xp 00000000 08:05 3719568                    /usr/lib/libgio-2.0.so.0.0.0
7f461cad5000-7f461ccd5000 ---p 0006e000 08:05 3719568                    /usr/lib/libgio-2.0.so.0.0.0
7f461ccd5000-7f461ccd8000 rwxp 0006e000 08:05 3719568                    /usr/lib/libgio-2.0.so.0.0.0
7f461ccd8000-7f461ce15000 r-xp 00000000 08:05 3719732                    /usr/lib/libxml2.so.2.6.31
7f461ce15000-7f461d015000 ---p 0013d000 08:05 3719732                    /usr/lib/libxml2.so.2.6.31
7f461d015000-7f461d01e000 rwxp 0013d000 08:05 3719732                    /usr/lib/libxml2.so.2.6.31
7f461d01e000-7f461d01f000 rwxp 7f461d01e000 00:00 0 
7f461d01f000-7f461d057000 r-xp 00000000 08:05 3720606                    /usr/lib/libcroco-0.6.so.3.0.1
7f461d057000-7f461d256000 ---p 00038000 08:05 3720606                    /usr/lib/libcroco-0.6.so.3.0.1
7f461d256000-7f461d25a000 rwxp 00037000 08:05 3720606                    /usr/lib/libcroco-0.6.so.3.0.1
7f461d25a000-7f461d291000 r-xp 00000000 08:05 3719411                    /usr/lib/libgsf-1.so.114.0.7
7f461d291000-7f461d490000 ---p 00037000 08:05 3719411                    /usr/lib/libgsf-1.so.114.0.7
7f461d490000-7f461d494000 rwxp 00036000 08:05 3719411                    /usr/lib/libgsf-1.so.114.0.7
7f461d494000-7f461d495000 rwxp 7f461d494000 00:00 0 
7f461d495000-7f461d4c9000 r-xp 00000000 08:05 3720633                    /usr/lib/librsvg-2.so.2.22.2
7f461d4c9000-7f461d6c9000 ---p 00034000 08:05 3720633                    /usr/lib/librsvg-2.so.2.22.2
7f461d6c9000-7f461d6cb000 rwxp 00034000 08:05 3720633                    /usr/lib/librsvg-2.so.2.22.2
7f461d6d1000-7f461d6d2000 rwxs 81000000 00:0e 12734                      /dev/snd/pcmC0D0p
7f461d6d2000-7f461d6d3000 r-xs 80000000 00:0e 12734                      /dev/snd/pcmC0D0p
7f461d6d3000-7f461d6d4000 rwxs 00000000 00:09 48594956                   /SYSV0056a4d5 (deleted)
7f461d6d4000-7f461d6d5000 rwxs 00000000 00:09 48168971                   /SYSV00000000 (deleted)
7f461d6d5000-7f461d6d6000 rwxs 00000000 00:09 48136202                   /SYSV00000000 (deleted)
7f461d6d6000-7f461d6da000 rwxs 618de000 00:0e 13913                      /dev/nvidia0
7f461d6da000-7f461d6de000 rwxs 3425d000 00:0e 13913                      /dev/nvidia0
7f461d6de000-7f461d6df000 rwxs e0550000 00:0e 13913                      /dev/nvidia0
7f461d6df000-7f461d6e0000 rwxs 3cafd000 00:0e 13913                      /dev/nvidia0
7f461d6e0000-7f461d6e1000 rwxs 42ae0000 00:0e 13913                      /dev/nvidia0
7f461d6e1000-7f461d6e2000 rwxs fd641000 00:0e 13913                      /dev/nvidia0
7f461d6e2000-7f461d6e3000 rwxs 6edf2000 00:0e 13913                      /dev/nvidia0
7f461d6e3000-7f461d6e5000 r-xp 00000000 08:05 3785185                    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f461d6e5000-7f461d8e4000 ---p 00002000 08:05 3785185                    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f461d8e4000-7f461d8e5000 rwxp 00001000 08:05 3785185                    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f461d8e5000-7f461d945000 rwxs 00000000 00:09 48070664                   /SYSV00000000 (deleted)
7f461d945000-7f461dbd6000 r-xp 00000000 08:05 4047009                    /usr/share/icons/hicolor/icon-theme.cache
7f461dbd6000-7f461e346000 r-xp 00000000 08:05 4047799                    /usr/share/icons/gnome/icon-theme.cache
7f461e346000-7f461e3f1000 r-xp 00000000 08:05 4049377                    /usr/share/icons/Tangerine/icon-theme.cache
7f461e3f1000-7f461e557000 r-xp 00000000 08:05 4047926                    /usr/share/icons/Human/icon-theme.cache
7f461e557000-7f461e65b000 rwxp 7f461e557000 00:00 0 
7f461e65b000-7f461e65d000 r-xp 00000000 08:05 4000133                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f461e65d000-7f461e85c000 ---p 00002000 08:05 4000133                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f461e85c000-7f461e85d000 rwxp 00001000 08:05 4000133                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f461e85d000-7f461e8ee000 r-xp 00000000 08:05 3932346                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f461e8ee000-7f461e8f7000 r-xs 00000000 08:05 2098919                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
7f461e8f7000-7f461e8fb000 r-xs 00000000 08:05 2098913                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
7f461e8fb000-7f461e904000 r-xs 00000000 08:05 2098918                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
7f461e904000-7f461e90f000 r-xs 00000000 08:05 2098917                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
7f461e90f000-7f461e93d000 r-xs 00000000 08:05 2098927                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
7f461e93d000-7f461e941000 r-xp 00000000 08:05 1179661                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f461e941000-7f461eb41000 ---p 00004000 08:05 1179661                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f461eb41000-7f461eb42000 rwxp 00004000 08:05 1179661                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f461eb42000-7f461eb54000 r-xp 00000000 08:05 3784892                    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
7f461eb54000-7f461ed5400Aborted
```

---

### Post by Dark Aspect on 2009-12-05
Sorry to bring back an old(er) thread but I have the same problem and here is the fix. Delete the 005-Lune folder, you'll only lose two or three high res textures and it won't crash.

---

### Post by grossaffe on 2009-12-22
> **Dark Aspect said:**
> Sorry to bring back an old(er) thread but I have the same problem and here is the fix. Delete the 005-Lune folder, you'll only lose two or three high res textures and it won't crash.

don't apologize for bumping this thread, I'm happy to have it resolved.  I guess I should've just gone with my gut and deleted the last texture, huh (or I guess the whole folder since you don't want a half-done moon)

---

