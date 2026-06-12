---
title: "Gens/GS r7_pre2 - Preview Release"
date: 2009-07-28
forum: Emulators
---

### Post by GerbilSoft on 2009-07-28
[s]I finally got the new plugin system in Gens/GS to a point where I can call it v1.0. However, I'm not quite done with Gens/GS r7. So, I'm releasing an almost-done preview release, r7_pre2.[/s]

[s]Gens/GS r7_pre3 is out now, with fixes for some bugs that crashed the emulator in some situations. (Also, I added a page for mdp_error.h in the MDP documentation.)[/s]

[s]Gens/GS r7_pre4 is out now. Release 7 won't be out until I finish the documentation, but there's a ton of useful bug fixes in r7_pre4, including a fix for an SRAM regression introduced in r7_pre2 and proper POV hat support on Linux. (I have no idea why the Ubuntu developers decided to use POV hats on 9.04, but whatever.)[/s]

Gens/GS r7_pre5 is out now. I really didn't want to do another prerelease, but this has a ton of changes, including fixes for inverted axes in Controller Configuration on the Linux version, plus a fix with POV hats on the Linux version. Additionally, RGB color scaling is now supported, so, for example, an MD CRAM color 0xEEE is scaled to RGB(255,255,255) instead of RGB(224,224,224). This results in brighter images, and is more accurate to how the actual hardware works. (0xEEE tells the VDP to output maximum brightness for all three color components.) [This can be turned off in Graphics, Color Adjust.]

[img]http://www.soniccenter.org/gerbilsoft/gens/r7_pre5/gens-gs-r7_pre5.png[/img]

Please test it and report any bugs you may find.

Changes from m6 to r7_pre5: [http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=blob;f=NEWS.txt;hb=release-7_pre5](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=blob;f=NEWS.txt;hb=release-7_pre5)

Downloads:[list]
[*]Source Code: [gens-gs-r7_pre5.tar.gz]("http://www.soniccenter.org/gerbilsoft/gens/r7_pre5/gens-gs-r7_pre5.tar.gz")
[*]Ubuntu 8.04+ (i386): [gens_2.16.6.95_i386.deb]("http://www.soniccenter.org/gerbilsoft/gens/r7_pre5/gens_2.16.6.95_i386.deb")
[*]Win32 (i386): [gens-gs-r7_pre5-win32.zip]("http://www.soniccenter.org/gerbilsoft/gens/r7_pre5/gens-gs-r7_pre5-win32.zip")
[/list]

EDIT: Release 7, Preview 5 is out. :)

---

### Post by mocha on 2009-07-29
Do you still use the site [http://info.sonicretro.org/Gens/GS]("http://info.sonicretro.org/Gens/GS")?  I just happened to come across this post by accident but was always trying to follow the development of gens at the sonicretro site.

---

### Post by mister_k81 on 2009-07-29
Nice to see you continue work on this emulator. 

Anyway, I tried it and the first thing that happened on start up was that it crashed, giving me this error message:

```
b66bb000-b66bc000 rw-gens:1:gens_sighandler(): Signal 6 (SIGABRT) received. Shutting down.
``` 

But this issue was solved simply by deleting my .gens directory for Gens/GS milestone 6. 
 
The second time it crashed on me was when I tried to change the OpenGL custom resolution settings. It gave me the following error message: 

```
*** stack smashing detected ***: gens terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb75dada8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb75dad60]
gens[0x80bcf4a]
gens[0x80cadab]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__INT+0x8c)[0xb78c40ec]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb78b6c7b]
/usr/lib/libgobject-2.0.so.0[0xb78cce57]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb78ce4b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb78ce936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_dialog_response+0x91)[0xb7b44b31]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb78c43a4]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb78b6c7b]
/usr/lib/libgobject-2.0.so.0[0xb78cce57]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb78ce4b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb78ce936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_clicked+0x8a)[0xb7b12bda]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b141f8]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb78c43a4]
/usr/lib/libgobject-2.0.so.0[0xb78b53d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb78b6c7b]
/usr/lib/libgobject-2.0.so.0[0xb78cc6c0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb78ce4b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb78ce936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_released+0x8a)[0xb7b12c7a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b12cb3]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bcd526]
/usr/lib/libgobject-2.0.so.0[0xb78b53d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb78b6c7b]
/usr/lib/libgobject-2.0.so.0[0xb78ccaff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb78ce34f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb78ce936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7ce82ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xec)[0xb7bc5f7c]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2e7)[0xb7bc7327]
/usr/lib/libgdk-x11-2.0.so.0[0xb7a5434a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb7829b88]
/usr/lib/libglib-2.0.so.0[0xb782d0eb]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x68)[0xb782d268]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_iteration_do+0x33)[0xb7bc75c3]
gens[0x80ba5c4]
gens[0x80ba6a7]
gens[0x8050b81]
gens[0x80b5c12]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb74f3775]
gens[0x80504e1]
======= Memory map: ========
08048000-08238000 r-xp 00000000 08:11 26271      /usr/bin/gens
08238000-0824d000 rw-p 001f0000 08:11 26271      /usr/bin/gens
0824d000-0930d000 rw-p 0824d000 00:00 0 
0a459000-0a8df000 rw-p 0a459000 00:00 0          [heap]
b47b6000-b48eb000 r-xp 00000000 08:11 10338      /usr/lib/libxml2.so.2.6.32
b48eb000-b48ec000 ---p 00135000 08:11 10338      /usr/lib/libxml2.so.2.6.32
b48ec000-b48f0000 r--p 00135000 08:11 10338      /usr/lib/libxml2.so.2.6.32
b48f0000-b48f1000 rw-p 00139000 08:11 10338      /usr/lib/libxml2.so.2.6.32
b48f1000-b48f2000 rw-p b48f1000 00:00 0 
b48f2000-b4923000 r-xp 00000000 08:11 9527       /usr/lib/libcroco-0.6.so.3.0.1
b4923000-b4926000 rw-p 00030000 08:11 9527       /usr/lib/libcroco-0.6.so.3.0.1
b4926000-b4959000 r-xp 00000000 08:11 9804       /usr/lib/libgsf-1.so.114.0.11
b4959000-b495a000 ---p 00033000 08:11 9804       /usr/lib/libgsf-1.so.114.0.11
b495a000-b495c000 r--p 00033000 08:11 9804       /usr/lib/libgsf-1.so.114.0.11
b495c000-b495d000 rw-p 00035000 08:11 9804       /usr/lib/libgsf-1.so.114.0.11
b495d000-b495e000 rw-p b495d000 00:00 0 
b495e000-b498f000 r-xp 00000000 08:11 10182      /usr/lib/librsvg-2.so.2.26.0
b498f000-b4990000 r--p 00031000 08:11 10182      /usr/lib/librsvg-2.so.2.26.0
b4990000-b4991000 rw-p 00032000 08:11 10182      /usr/lib/librsvg-2.so.2.26.0
b49a6000-b49c0000 r--s 00000000 08:11 28246      /usr/share/mime/mime.cache
b49c0000-b49da000 r-xp 00000000 08:11 50788      /usr/lib/gio/modules/libgvfsdbus.so
b49da000-b49db000 r--p 00019000 08:11 50788      /usr/lib/gio/modules/libgvfsdbus.so
b49db000-b49dc000 rw-p 0001a000 08:11 50788      /usr/lib/gio/modules/libgvfsdbus.so
b49dc000-b4a12000 r-xp 00000000 08:11 137181     /lib/libdbus-1.so.3.4.0
b4a12000-b4a13000 r--p 00035000 08:11 137181     /lib/libdbus-1.so.3.4.0
b4a13000-b4a14000 rw-p 00036000 08:11 137181     /lib/libdbus-1.so.3.4.0
b4a14000-b4a26000 r-xp 00000000 08:11 30294      /usr/lib/libgvfscommon.so.0.0.0
b4a26000-b4a27000 r--p 00012000 08:11 30294      /usr/lib/libgvfscommon.so.0.0.0
b4a27000-b4a28000 rw-p 00013000 08:11 30294      /usr/lib/libgvfscommon.so.0.0.0
b4a29000-b4a38000 r-xp 00000000 08:11 2579       /lib/libbz2.so.1.0.4
b4a38000-b4a39000 r--p 0000f000 08:11 2579       /lib/libbz2.so.1.0.4
b4a39000-b4a3a000 rw-p 00010000 08:11 2579       /lib/libbz2.so.1.0.4
b4a3a000-b4a3b000 r-xp 00000000 08:11 12704      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b4a3b000-b4a3c000 r--p 00000000 08:11 12704      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b4a3c000-b4a3d000 rw-p 00001000 08:11 12704      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b4a3d000-b4a4c000 r-xp 00000000 08:11 34819      /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4a4c000-b4a4d000 r--p 0000e000 08:11 34819      /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4a4d000-b4a4e000 rw-p 0000f000 08:11 34819      /usr/lib/gio/modules/libgioremote-volume-monitor.so
b4a4e000-b4df5000 r--p 00000000 08:11 11611      /usr/share/icons/hicolor/icon-theme.cache
b4df5000-b4f75000 rw-s d3e08000 00:0f 7754       /dev/nvidia0
b4f75000-b50f5000 rw-s d3e08000 00:0f 7754       /dev/nvidia0
b50f5000-b5275000 rw-s d043c000 00:0f 7754       /dev/nvidia0
b5275000-b52d5000 rw-s 00000000 00:09 11993115   /SYSV00000000 (deleted)
b5326000-b53a7000 rw-p b5326000 00:00 0 
b53a7000-b53a8000 rw-s 00000000 00:09 11960346   /SYSV00000000 (deleted)
b53a8000-b53a9000 rw-s 00000000 00:09 11927577   /SYSV00000000 (deleted)
b53ab000-b53ac000 r--s 00000000 08:11 26119      /home/kev/.local/share/mime/mime.cache
b53ac000-b53ad000 rw-s 00000000 00:09 11894808   /SYSV00000000 (deleted)
b53ad000-b54ad000 rw-s e0114000 00:0f 7754       /dev/nvidia0
b54ad000-b54ae000 rw-s d3f8c000 00:0f 7754       /dev/nvidia0
b54ae000-b54af000 rw-s 1eaee000 00:0f 7754       /dev/nvidia0
b54af000-b54b0000 rw-s 1eaed000 00:0f 7754       /dev/nvidia0
b54b0000-b54b1000 rw-s de820000 00:0f 7754       /dev/nvidia0
b54b1000-b55b3000 rw-s e0011000 00:0f 7754       /dev/nvidia0
b55f4000-b5657000 rw-p 00000000 00:0f 743        /dev/zero
b5657000-b5a8f000 rw-s d0000000 00:0f 7754       /dev/nvidia0
b5a8f000-b5ab9000 rw-s 00000000 00:09 0          /SYSV00000000 (deleted)
b5ab9000-b5b19000 rw-s 00000000 00:09 11862039   /SYSV00000000 (deleted)
b5b19000-b5bb1000 r--p 00000000 08:11 42100      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5bb1000-b5bb3000 r-xp 00000000 08:11 18012      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5bb3000-b5bb4000 r--p 00001000 08:11 18012      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5bb4000-b5bb5000 rw-p 00002000 08:11 18012      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5bb5000-b5bbb000 r--s 00000000 08:11 107224     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5bbb000-b5bbe000 r--s 00000000 08:11 107233     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b5bbe000-b5bc1000 r--s 00000000 08:11 117703     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b5bc1000-b5bc2000 r--s 00000000 08:11 107219     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5bc2000-b5bc5000 r--s 00000000 08:11 107225     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5bc5000-b5bcc000 r--s 00000000 08:11 126177     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5bcc000-b5bcf000 r--s 00000000 08:11 107231     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5bcf000-b5bd7000 r--s 00000000 08:11 107234     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5bd7000-b5be2000 r--s 00000000 08:11 107214     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5be2000-b5be4000 r--s 00000000 08:11 107230     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b5be4000-b5be5000 r--s 00000000 08:11 107217     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b5be5000-b5c07000 r--s 00000000 08:11 122586     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5c07000-b5c0e000 r--s 00000000 08:11 107228     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5c0e000-b5c14000 r--s 00000000 08:11 107213     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5c14000-b5c1b000 r--s 00000000 08:11 120311     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5c1b000-b5c1d000 r--s 00000000 08:11 122587     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b5c1d000-b5c21000 r--s 00000000 08:11 35395      /home/kev/.fontconfig/7d19654197fba6a1bdf14444e1602296-x86.cache-2
b5c21000-b5c22000 r-xp 00000000 08:11 28280      /usr/lib/mdp/mdp_render_super_eagle.so
b5c22000-b5c23000 rw-p 00000000 08:11 28280      /usr/lib/mdp/mdp_render_super_eagle.so
b5c23000-b5c24000 r-xp 00000000 08:11 28284      /usr/lib/mdp/mdp_render_super_2xsai.so
b5c24000-b5c25000 rw-p 00001000 08:11 28284      /usr/lib/mdp/mdp_render_super_2xsai.so
b5c25000-b5c26000 r-xp 00000000 08:11 28278      /usr/lib/mdp/mdp_render_scanline_50.so
b5c26000-b5c27000 rw-p 00000000 08:11 28278      /usr/lib/mdp/mdp_render_scanline_50.so
b5c27000-b5c28000 r-xp 00000000 08:11 28301      /usr/lib/mdp/mdp_render_scanline_25.so
b5c28000-b5c29000 rw-p 00001000 08:11 28301      /usr/lib/mdp/mdp_render_scanline_25.so
b5c29000-b5c2a000 r-xp 00000000 08:11 26928      /usr/lib/mdp/mdp_render_scanline.so
b5c2a000-b5c2b000 rw-p 00000000 08:11 26928      /usr/lib/mdp/mdp_render_scanline.so
b5c2b000-b5c2e000 r-xp 00000000 08:11 26292      /usr/lib/mdp/mdp_render_scale4x.so
b5c2e000-b5c2f000 rw-p 00002000 08:11 26292      /usr/lib/mdp/mdp_render_scale4x.so
b5c2f000-b5c31000 r-xp 00000000 08:11 26861      /usr/lib/mdp/mdp_render_scale3x.so
b5c31000-b5c32000 rw-p 00001000 08:11 26861      /usr/lib/mdp/mdp_render_scale3x.so
b5c32000-b5c34000 r-xp 00000000 08:11 27260      /usr/lib/mdp/mdp_render_scale2x.so
b5c34000-b5c35000 rw-p 00001000 08:11 27260      /usr/lib/mdp/mdp_render_scale2x.so
b5c35000-b5c36000 r-xp 00000000 08:11 28275      /usr/lib/mdp/mdp_render_interpolated_scanline_50.so
b5c36000-b5c37000 rw-p 00001000 08:11 28275      /usr/lib/mgens:1:gens_sighandler(): Signal 6 (SIGABRT) received. Shutting down. 

```

The custom resolution settings worked fine for me in milestone 6. But here it crashes if I put in anything other than the pre-defined OpenGL resolutions that are already listed in the options menu. 

Other than those two problems, everything else seems to be working pretty well so far.

---

### Post by GerbilSoft on 2009-07-29
> **mocha said:**
> Do you still use the site [http://info.sonicretro.org/Gens/GS]("http://info.sonicretro.org/Gens/GS")?  I just happened to come across this post by accident but was always trying to follow the development of gens at the sonicretro site.
I haven't updated the Gens/GS page on Sonic Retro yet, since this is a preview release. It will probably be updated sometime later this week.

> **mister_k81 said:**
> 
```
*** stack smashing detected ***: gens terminated
```

I reproduced this on my local system using the debug build, which has stack smashing prevention enabled. Seems like something's wrong with the OpenGL resolution dialog. I'll take a look at it and try to fix it.

EDIT: Fixed in commit 2d86a7ff4a1cdc594c6deaa961a9bdd56eb82402: [http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=2d86a7ff4a1cdc594c6deaa961a9bdd56eb82402;hp=4b0026690238ba86ffc948ea6bde785849b66c80](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=2d86a7ff4a1cdc594c6deaa961a9bdd56eb82402;hp=4b0026690238ba86ffc948ea6bde785849b66c80)

---

### Post by BigSilly on 2009-07-29
Same here. First I deleted the .gens folder as mentioned above, then tried to set a custom resolution of 1440x900 for my monitor, but it crashed with

```
Gens/GS has crashed with Signal 6.
SIGABRT: Aborted.
```

And now I get that whenever I start it. Hope this helps.

---

### Post by wingnux on 2009-07-29
Thank you very much!! =)

---

### Post by GerbilSoft on 2009-07-29
I fixed the problem. If you're compiling from source, you can apply this patch:

```

commit 2d86a7ff4a1cdc594c6deaa961a9bdd56eb82402
Author: David Korth <gerbilsoft@verizon.net>
Date:   Wed Jul 29 04:18:21 2009 -0400

    [GTK+] gens_window_sync.cpp: Fixed an off-by-one in Sync_Gens_Window_GraphicsMenu().
    
    If a custom resolution was set, the custom resolution code ended up writing
    past the end of sCustomRes[], resulting in a stack smash.
    
    This bug was reported by mister_k81 on the Ubuntu Forums:
    http://ubuntuforums.org/showpost.php?p=7696449&postcount=3

diff --git a/src/gens/ui/gtk/gens/gens_window_sync.cpp b/src/gens/ui/gtk/gens/gens_window_sync.cpp
index e89bda1..7924169 100644
--- a/src/gens/ui/gtk/gens/gens_window_sync.cpp
+++ b/src/gens/ui/gtk/gens/gens_window_sync.cpp
@@ -303,7 +303,7 @@ void Sync_Gens_Window_GraphicsMenu(void)
 		// Custom resolution. Set the text.
 		char sCustomRes[32];
 		snprintf(sCustomRes, sizeof(sCustomRes), "Custom... (%dx%d)", Video.GL.width, Video.GL.height);
-		sCustomRes[sizeof(sCustomRes)] = 0x00;
+		sCustomRes[sizeof(sCustomRes)-1] = 0x00;
 		gtk_label_set_text(GTK_LABEL(gtk_bin_get_child(GTK_BIN(mnuGLResCustom))), sCustomRes);
 	}
 	else

```

---

### Post by wingnux on 2009-07-29
It crashes on my system when I switch to fullscreen while using the sdl+opengl backend. When I switch to the SDL backend it runs just fine but I can't get any filter to work on fullscreen =/

Here's the error message:

> Gens/GS has crashed with Signal 11.
SIGSEGV: Segmentation fault.

I'm running it on Ubuntu Jaunty 32bit, nVIDIA 8800GS card with the latest beta drivers installed and compiz-fusion running.

---

### Post by spcwingo on 2009-07-29
Thanks for this...running great with SDL backend on my Athlon XP/GeForce 6200 (with Nvidia 173 driver) setup.

---

### Post by GerbilSoft on 2009-07-29
> **wingnux said:**
> It crashes on my system when I switch to fullscreen while using the sdl+opengl backend. When I switch to the SDL backend it runs just fine but I can't get any filter to work on fullscreen =/

Here's the error message:



I'm running it on Ubuntu Jaunty 32bit, nVIDIA 8800GS card with the latest beta drivers installed and compiz-fusion running.
Can you try to get a backtrace with gdb? (You might have to recompile with debugging symbols enabled.)

Also, try setting the internal color depth to 16-bit. I've noticed some issues with 32-bit OpenGL surfaces on my system in fullscreen. [Graphics, Bits per pixel, 16 (565)]

---

### Post by disturbedite on 2009-07-29
lots of really great updates in this one. i'll have to try it out.

---

### Post by wingnux on 2009-07-29
> **GerbilSoft said:**
> Can you try to get a backtrace with gdb? (You might have to recompile with debugging symbols enabled.)

Also, try setting the internal color depth to 16-bit. I've noticed some issues with 32-bit OpenGL surfaces on my system in fullscreen. [Graphics, Bits per pixel, 16 (565)]

Setting it to 16-bit worked, thank you very much! Also, I've discovered that I can get full screen filtering enabled when selecting them via the keyboard (F11/F12) and after that they work properly even if I restart gens. :P

---

### Post by GerbilSoft on 2009-07-29
> **wingnux said:**
> Setting it to 16-bit worked, thank you very much! Also, I've discovered that I can get full screen filtering enabled when selecting them via the keyboard (F11/F12) and after that they work properly even if I restart gens. :P
Ok, then this is because the nVidia driver doesn't provide 32-bit GLX visuals in fullscreen. I'm using an ATI FireGL V5200 (RV530) with the Mesa drivers, and it has the same issue.

Well, either that, or Gens/GS isn't allocating it properly. I'll figure out what's going on later. Eventually, it'll "fall back" to lower color depth so it'll "just work" without crashing. (I already implemented this for backend switching; I need to implement it for fullscreen switching and fullscreen resolutions.)

EDIT: I figured out the problem. Gens/GS was specifying 32-bit color depth for the GLX visual instead of 24-bit. This seemed to work in windowed mode, but failed horribly in fullscreen. Note that the color depth here only applies to the actual color components, and doesn't include the alpha channels. This has been fixed in commit [dc1bf7d33073bae3b6be2f98bab6928b1d5edce5](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commit;h=dc1bf7d33073bae3b6be2f98bab6928b1d5edce5), but that commit depends on an earlier commit that cleaned up a part of the SDL+OpenGL backend. Here's a combined patch.

```

diff --git a/src/gens/video/vdraw_sdl_gl.c b/src/gens/video/vdraw_sdl_gl.c
index 76f3b1f..3bb032f 100644
--- a/src/gens/video/vdraw_sdl_gl.c
+++ b/src/gens/video/vdraw_sdl_gl.c
@@ -186,6 +186,30 @@ int vdraw_sdl_gl_init(void)
 
 
 /**
+ * vdraw_sdl_gl_set_visual(): Set OpenGL visual attributes.
+ * @param depth Color depth.
+ * @param r Red bits.
+ * @param g Green bits.
+ * @param b Blue bits.
+ * @param a Alpha bits.
+ * @param format Pixel format.
+ * @param type Data type.
+ */
+static inline void vdraw_sdl_gl_set_visual(unsigned int depth,
+					   unsigned int r, unsigned int g, unsigned int b, unsigned int a,
+					   GLenum format, GLenum type)
+{
+	SDL_GL_SetAttribute(SDL_GL_DEPTH_SIZE, depth);
+	SDL_GL_SetAttribute(SDL_GL_RED_SIZE,   r);
+	SDL_GL_SetAttribute(SDL_GL_GREEN_SIZE, g);
+	SDL_GL_SetAttribute(SDL_GL_BLUE_SIZE,  b);
+	SDL_GL_SetAttribute(SDL_GL_ALPHA_SIZE, a);
+	m_pixelFormat = format;
+	m_pixelType = type;
+}
+
+
+/**
  * vdraw_sdl_gl_init_opengl(): Initialize the OpenGL backend.
  * @param w Width.
  * @param h Height.
@@ -196,42 +220,27 @@ static int vdraw_sdl_gl_init_opengl(const int w, const int h, const BOOL reinitS
 {
 	if (reinitSDL)
 	{
-		// Enable double buffering.
+		// Set various OpenGL attributes.
 		SDL_GL_SetAttribute(SDL_GL_DOUBLEBUFFER, 1);
 		
 		// Color depth values.
 		if (bppOut == 15)
 		{
 			// 15-bit color. (Mode 555)
-			SDL_GL_SetAttribute(SDL_GL_DEPTH_SIZE, 15);
-			SDL_GL_SetAttribute(SDL_GL_RED_SIZE,    5);
-			SDL_GL_SetAttribute(SDL_GL_GREEN_SIZE,  5);
-			SDL_GL_SetAttribute(SDL_GL_BLUE_SIZE,   5);
-			SDL_GL_SetAttribute(SDL_GL_ALPHA_SIZE,  0);
-			m_pixelType = GL_UNSIGNED_SHORT_1_5_5_5_REV;
-			m_pixelFormat = GL_BGRA;
+			vdraw_sdl_gl_set_visual(15, 5, 5, 5, 0, GL_BGRA,
+						GL_UNSIGNED_SHORT_1_5_5_5_REV);
 		}
 		else if (bppOut == 16)
 		{
 			// 16-bit color. (Mode 565)
-			SDL_GL_SetAttribute(SDL_GL_DEPTH_SIZE, 16);
-			SDL_GL_SetAttribute(SDL_GL_RED_SIZE,    5);
-			SDL_GL_SetAttribute(SDL_GL_GREEN_SIZE,  6);
-			SDL_GL_SetAttribute(SDL_GL_BLUE_SIZE,   5);
-			SDL_GL_SetAttribute(SDL_GL_ALPHA_SIZE,  0);
-			m_pixelType = GL_UNSIGNED_SHORT_5_6_5;
-			m_pixelFormat = GL_RGB;
+			vdraw_sdl_gl_set_visual(16, 5, 6, 5, 0, GL_RGB,
+						GL_UNSIGNED_SHORT_5_6_5);
 		}
 		else //if (bppOut == 32)
 		{
 			// 32-bit color.
-			SDL_GL_SetAttribute(SDL_GL_DEPTH_SIZE, 32);
-			SDL_GL_SetAttribute(SDL_GL_RED_SIZE,    8);
-			SDL_GL_SetAttribute(SDL_GL_GREEN_SIZE,  8);
-			SDL_GL_SetAttribute(SDL_GL_BLUE_SIZE,   8);
-			SDL_GL_SetAttribute(SDL_GL_ALPHA_SIZE,  0);
-			m_pixelType = GL_UNSIGNED_BYTE;
-			m_pixelFormat = GL_BGRA;
+			vdraw_sdl_gl_set_visual(24, 8, 8, 8, 0, GL_BGRA,
+						GL_UNSIGNED_BYTE);
 		}
 		
 		vdraw_sdl_gl_screen = SDL_SetVideoMode(w, h, 0, VDRAW_SDL_GL_FLAGS | (vdraw_get_fullscreen() ? SDL_FULLSCREEN : 0));
@@ -239,9 +248,10 @@ static int vdraw_sdl_gl_init_opengl(const int w, const int h, const BOOL reinitS
 		{
 			// Error setting the SDL video mode.
 			const char *sErr = SDL_GetError();
-			SDL_QuitSubSystem(SDL_INIT_VIDEO);
 			LOG_MSG(video, LOG_MSG_LEVEL_ERROR,
 				"SDL_SetVideoMode() failed: %s", sErr);
+			
+			SDL_QuitSubSystem(SDL_INIT_VIDEO);
 			return -1;
 		}
 	}

```

---

### Post by mister_k81 on 2009-07-29
> **GerbilSoft said:**
> I fixed the problem. If you're compiling from source, you can apply this patch:


It took me a while to figure out how to patch this (I have very limited experience with compiling code), but I eventually did manage to get both patches to work :D ...

Anyway, I built it from source and installed with checkinstall, and the custom resolution bug seems to be fixed now. Also, this version of GensGS doesn't crash anymore if I use my old .gens config folder (from release 6). I'm guessing that the custom resolution listed in the gens.cfg file was making it crash on start up.

However, I also noticed another issue... while running in a custom resolution, Genesis games only seem to run at 30fps. But this only happens if I run in either 15 or 32 bits per pixel mode with "full stretch" turned on. Turning off full stretch will make games run at 60fps again. But, using full stretch in 16bpp mode has little to no effect to the framerate at all. This problem wasn't there for me in milestone 6.

**Edit**

OK, I should also add something else, that the frame rate issue seems to happen when I have VSync and "Full Stretch" on at the same time while running in either 15bpp or 32bpp with a custom resolution.

---

### Post by GerbilSoft on 2009-07-29
> **mister_k81 said:**
> 
However, I also noticed another issue... while running in a custom resolution, Genesis games only seem to run at 30fps. But this only happens if I run in either 15 or 32 bits per pixel mode with "full stretch" turned on. Turning off full stretch will make games run at 60fps again. But, using full stretch in 16bpp mode has little to no effect to the framerate at all. This problem wasn't there for me in milestone 6.

**Edit**

OK, I should also add something else, that the frame rate issue seems to happen when I have VSync and "Full Stretch" on at the same time while running in either 15bpp or 32bpp with a custom resolution.
15-bit color (aka "555") seems to be horribly slow on all Linux video drivers, probably because no one uses it. I'd recommend using 16-bit color (aka "565") instead.

32-bit color also seems to be slow in some cases (especially when using a renderer that scales to larger than 2x). I'd recommend using 16-bit color in this case. Remember, the Sega Genesis could only output 9-bit color, so even with 16-bit, you aren't losing any precision. (32X could output 15-bit color, but that's automatically converted to 16-bit in the rendering code.)

Random note: 15-bit vs. 16-bit is mostly a Windows legacy issue. Some video drivers that advertised 16-bit color didn't really support 16-bit (565), and only supported 15-bit (555). OpenGL doesn't have this issue, but I left the color depth selection in for debugging purposes.

---

### Post by mister_k81 on 2009-07-30
> **GerbilSoft said:**
> 15-bit color (aka "555") seems to be horribly slow on all Linux video drivers, probably because no one uses it. I'd recommend using 16-bit color (aka "565") instead.

32-bit color also seems to be slow in some cases (especially when using a renderer that scales to larger than 2x). I'd recommend using 16-bit color in this case. Remember, the Sega Genesis could only output 9-bit color, so even with 16-bit, you aren't losing any precision. (32X could output 15-bit color, but that's automatically converted to 16-bit in the rendering code.)

Random note: 15-bit vs. 16-bit is mostly a Windows legacy issue. Some video drivers that advertised 16-bit color didn't really support 16-bit (565), and only supported 15-bit (555). OpenGL doesn't have this issue, but I left the color depth selection in for debugging purposes.

Ah, OK. I generally just stick with the 16bpp mode anyway, because as you've said, there is no real difference between 16 and 32 visually, and 16bpp does get better performance. It's not really a problem to me though, I only brought it up because it's something that I haven't noticed before in the previous builds. It just seemed like it could've been a potential bug.

---

### Post by ZombieRyushu on 2009-07-31
I have a couple issues. 

The Sega CD crashing issue has not been fixed. (That same crash I reported before still crashes the system.

The emulator is not starting in full screen mode.

For some reason mine ws giving me the error "Cannot find /usr/lib/mvp" The 32-bit plugins were installed in /usr/lib, SHOULD it be in /usr/lib/mvp?

Also save states from older versions are crashing the emulator.

---

### Post by GerbilSoft on 2009-07-31
I discussed this with you over IRC, but I'll reply here anyway for reference purposes.

> 
Also save states from older versions are crashing the emulator.

> 
The Sega CD crashing issue has not been fixed. (That same crash I reported before still crashes the system.

These were both buffer overflow errors that glibc only caught in the release build, which I wasn't testing. Fixed in commits [dc7837b8a83d938f919de7a4f3ced5148a386603](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=dc7837b8a83d938f919de7a4f3ced5148a386603) and [badf3aa21d55d06b53e1fad713a6f4d4084acd97](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=badf3aa21d55d06b53e1fad713a6f4d4084acd97), respectively.

> 
The emulator is not starting in full screen mode.

This was the incorrect GLX visuals for 32-bit color bug, fixed in commit [dc1bf7d33073bae3b6be2f98bab6928b1d5edce5](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=dc1bf7d33073bae3b6be2f98bab6928b1d5edce5).

> 
For some reason mine ws giving me the error "Cannot find /usr/lib/mvp" The 32-bit plugins were installed in /usr/lib, SHOULD it be in /usr/lib/mvp?

This is an odd bug with the autotools suite. I'll look into it.

---

### Post by OliW on 2009-07-31
I don't get any sound. But I didn't get any sound in the last stable release either.

I'm running karmic so that could well be the entire problem but it might be some audio config I've inadvertently brought through in my profile. Any ideas? Anyone on karmic with working sound in gens?

---

### Post by GerbilSoft on 2009-07-31
> **OliW said:**
> I don't get any sound. But I didn't get any sound in the last stable release either.

I'm running karmic so that could well be the entire problem but it might be some audio config I've inadvertently brought through in my profile. Any ideas? Anyone on karmic with working sound in gens?
If you're using PulseAudio, try turning it off. SDL (and Gens in particular) has issues with PulseAudio.

---

### Post by mocha on 2009-08-02
I've found setting SDL_AUDIODRIVER="esd" works well in Ubuntu.

---

### Post by GerbilSoft on 2009-08-02
I have released Gens/GS r7_pre3. It fixes the previously mentioned crash bugs and some other stuff.

---

### Post by Gocho on 2009-08-04
> **GerbilSoft said:**
> I have released Gens/GS r7_pre3. It fixes the previously mentioned crash bugs and some other stuff.

I downloaded the Source and tries to ./configure in my Ubuntu 9.04-amd64:

I get this:
```
configure: error: 64-bit is currently not supported.

```
](*,)

---

### Post by GerbilSoft on 2009-08-04
> **Gocho said:**
> I downloaded the Source and tries to ./configure in my Ubuntu 9.04-amd64:

I get this:
```
configure: error: 64-bit is currently not supported.

```
](*,)
Unfortunately, Gens/GS is currently not buildable on 64-bit (and non-x86) architectures due to the massive amount of x86 assembler. I'd suggest installing the 32-bit package using dpkg --force-architecture. (You'll need to install the 32-bit compatibility packages, too.)

---

### Post by BigSilly on 2009-08-05
I actually created a .deb for 64 bit using a script I got off the World of Goo forums! Don't ask me how it works, it just does. :D I've attached it anyway, and I'll add another post with the script I got.

Hope this helps anyway.

---

### Post by BigSilly on 2009-08-05
Here's the 32 to 64 bit .deb script. It's quite easy to use. :)  I'm no Linux expert at all, but this worked for me anyway.

EDIT: Sorry, rude of me. Here's the Read Me.

Attached is a shell script to convert the 32-bit Debian packages to 64-bit packages, if you prefer those. Unpack, mark executable, and run on the command line with the path to the 32-bit package as an argument. Like so:

username@username-desktop:~$ '/home/username/Downloads/deb-from-i386-to-amd64.sh'  '/home/username/Emulators/Gens_2.15.5-gs-m6-1_i386.deb'  Gens_2.15.5-gs-m6-1_amd64.deb

Obviously substitute the package there with whichever emulator or package you are wanting to use.

---

### Post by Gocho on 2009-08-05
> **BigSilly said:**
> I actually created a .deb for 64 bit using a script I got off the World of Goo forums! Don't ask me how it works, it just does. :D I've attached it anyway, and I'll add another post with the script I got.

Hope this helps anyway.


It works! Thanks BigSilly :D

---

### Post by superG on 2009-08-13
Downloaded r7_pre3 version: There are problems with joystick D-Pad (I am using Logitech Chillstream), I can't use diagonal directions (Up+Right for example), impossible to play.
There was such problem in original Gens, author advised to remove Gens configuration file and Reconfigure joystick, I have done this here, but problem still exists.
I can check PS3 joystick, if that's help.

---

### Post by GerbilSoft on 2009-08-13
> **superG said:**
> Downloaded r7_pre3 version: There are problems with joystick D-Pad (I am using Logitech Chillstream), I can't use diagonal directions (Up+Right for example), impossible to play.
There was such problem in original Gens, author advised to remove Gens configuration file and Reconfigure joystick, I have done this here, but problem still exists.
I can check PS3 joystick, if that's help.
I'm thinking that perhaps the gamepad is imitating a circular joystick with regards to diagonals.

Can you install SDLJoytest ([http://sdljoytest.sourceforge.net/](http://sdljoytest.sourceforge.net/)) and post what values it shows for all eight positions, plus center?

---

### Post by superG on 2009-08-14
> I'm thinking that perhaps the gamepad is imitating a circular joystick with regards to diagonals.

Can you install SDLJoytest ([http://sdljoytest.sourceforge.net/](http://sdljoytest.sourceforge.net/)) and post what values it shows for all eight positions, plus center? 

SDLJoytest shows only Axis0 and buttons, buttons are working, Axis0 mapped to first analog stick, as of D-Pad, it doesn't work.

Here is jstest output:
jstest /dev/input/js0 
Driver version is 2.1.0.
Joystick (Logitech Chillstream Controller) has 8 axes and 11 buttons.
Testing ... (interrupt to exit)
Axes:  0:     0  1:    -2  2:-32767  3:     0  4:    -2  5:-32767  6:     0  7:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 

6 axe is for left and right.
7 axe is for up and down.
left : 6 axe,-32767
right: 6 axe, 32767
up   : 7 axe,-32767
down : 7 axe, 32767

left, right, up, down works in Gens, but diagonal not :(

When I pressing up+left in jstest, it shows in 6 and 7 axis -32767 simultaneous.

---

### Post by GerbilSoft on 2009-08-14
> **superG said:**
> left, right, up, down works in Gens, but diagonal not :(

When I pressing up+left in jstest, it shows in 6 and 7 axis -32767 simultaneous.
Unfortunately, I'm not able to reproduce this. Using the Genesis I/O Sample Program ("Multitap - IO Sample Program (U) (Nov 28 1992).gen" in GoodGen), I see both U and L activated when holding Up+Left on my gamepads. Same for all four diagonal directions. (I'm using a Wii Classic Controller and a GameCube controller with an adapter.)

What game(s) are you playing that exhibit the no-diagonals problem when using a gamepad?

---

### Post by superG on 2009-08-15
> **GerbilSoft said:**
> 
What game(s) are you playing that exhibit the no-diagonals problem when using a gamepad?

Mortal Kombat 3 Ultimate, Snakes Rattle & Roll.

Just tried PS3 SIXAXIS, while giving perfect output on both jstest and on SDLJoytest, it's rather unusable on Gens, D-Pad controls are swapped, and you should press very hard, to see any input, the same thing with buttons (I think that's because sixaxis has analog buttons, and it reports different values based on how hard it's pressed).

I run I/O Sample Program on my Chillstream, and there is problems:
[in register dump table (2,1) position when counting from zero] D-Pad is lowest 4 bits, up is bit0, left is bit2, when I pressing them simultaneous, I am not getting 5 there; also when pressing any button of D-Pad, (3,1) byte is flickering.
SACBMXYZ works correctly.

I have analyzed input_sdl.c, and I think, problem can be here:

My D-Pad detected as POVHAT.

BOOL input_sdl_check_key_pressed(uint16_t key)

> case INPUT_JOYSTICK_TYPE_POVHAT:
{
	// Joystick POV hat.
	static const uint8_t povKeyToBit[4] = {SDL_HAT_UP, SDL_HAT_RIGHT, SDL_HAT_DOWN, SDL_HAT_LEFT};
	uint8_t povBit = povKeyToBit[INPUT_JOYSTICK_GET_POVHAT_DIRECTION(key)];
	
	if (INPUT_SDL_JOYSTICK_CHECK_POVHAT_DIRECTION(input_sdl_joy_state, joyNum, key, povBit))
		return TRUE;
	break;
}

I want to fix that thing, but unfortunately I spend hour compiling Gens/GS on my Ubuntu64 in 32-bit mode, and with no success. Quick & dirty I have edited configure.in, and tried adding -m32 switch to cflags_debug and CFLAGS, then autoreconf -fvi - no luck.

Maybe you know more clean ways, how to compile that on x86_64 Ubuntu, but in 32-bit mode?

---

### Post by GerbilSoft on 2009-08-15
> **superG said:**
> 
My D-Pad detected as POVHAT.

Interesting, since the Linux joystick system doesn't actually support POV hats. It only supports axes. I wonder why SDL is mapping it to a POV hat in this case.

In any case, I don't think that function is why diagonals aren't working. Can you get me the exact name of what Gens/GS detects the axes as? (i.e. in Controller Configuration, it should say things like "Joy 0, Axis Y-" and "Joy 0, Axis Y+".)

EDIT:

> **superG said:**
> 
Just tried PS3 SIXAXIS, while giving perfect output on both jstest and on SDLJoytest, it's rather unusable on Gens, D-Pad controls are swapped, and you should press very hard, to see any input, the same thing with buttons (I think that's because sixaxis has analog buttons, and it reports different values based on how hard it's pressed).

I reworked the function for SDL key configuration so it will hopefully improve configuration on controllers that have non-joystick axes, such as the SixAxis analog buttons. Specifically, the function takes the current state of the buttons, and only returns a value if the state changes to 0 and then to a non-zero value.

---

### Post by superG on 2009-08-16
> In any case, I don't think that function is why diagonals aren't working. Can you get me the exact name of what Gens/GS detects the axes as? (i.e. in Controller Configuration, it should say things like "Joy 0, Axis Y-" and "Joy 0, Axis Y+".)

Up: Joy 0, POV 0 Up
Down: Joy 0, POV 0 Down
Left: Joy 0, POV 0 Left
Right: Joy 0, POV 0 Right

BTW, I have tried Chillstream on Windows r7_pre3 version, D-Pad is fully working there, all diagonals, but anyway, there's used DInput backend, not SDL one.

---

### Post by GerbilSoft on 2009-08-16
> **superG said:**
> Up: Joy 0, POV 0 Up
Down: Joy 0, POV 0 Down
Left: Joy 0, POV 0 Left
Right: Joy 0, POV 0 Right

BTW, I have tried Chillstream on Windows r7_pre3 version, D-Pad is fully working there, all diagonals, but anyway, there's used DInput backend, not SDL one.
I'm not exactly sure why it's recognizing the controller input as POV hats, since Linux's joystick interface doesn't support it. (Or did you post the controller configuration information from the Windows version?)

In any case, all of my gamepads report standard axes for all controls on Linux, and diagonals work, so unfortunately I'm stuck here.

---

### Post by superG on 2009-08-16
> (Or did you post the controller configuration information from the Windows version?)
No, it's from Ubuntu.

---

### Post by GerbilSoft on 2009-08-16
> **superG said:**
> No, it's from Ubuntu.
Can you post your system information? i.e. Ubuntu version, architecture, USB devices, etc. I'm stuck here, and need to figure out what's going on before I can attempt to fix it. Also, library versions would be useful, i.e. what version of SDL and GTK+ you have installed.

---

### Post by superG on 2009-08-16
> Can you post your system information? i.e. Ubuntu version, architecture, USB devices, etc. I'm stuck here, and need to figure out what's going on before I can attempt to fix it. Also, library versions would be useful, i.e. what version of SDL and GTK+ you have installed.
Ubuntu 9.04, x86_64
A lot of usb dev's, scanner, printer, bluetooth dongle, mouse, keyboard, but only one joystick at a time, 4Gb RAM, Athlon64 4200+, GeForce.
gtk-2.16.1
SDL-1.2.13

Architecture isn't a problem, I just tried joystick and Gens on 32-bit architecture PC with Ubuntu 9.04, and same problem there.

---

### Post by GerbilSoft on 2009-08-16
> **superG said:**
> Ubuntu 9.04, x86_64
A lot of usb dev's, scanner, printer, bluetooth dongle, mouse, keyboard, but only one joystick at a time, 4Gb RAM, Athlon64 4200+, GeForce.
gtk-2.16.1
SDL-1.2.13

Architecture isn't a problem, I just tried joystick and Gens on 32-bit architecture PC with Ubuntu 9.04, and same problem there.
I'm using Ubuntu 8.04 as my test system. I'll install 9.04 in a VM tomorrow and see if it changes anything.

---

### Post by superG on 2009-08-16
> I'm using Ubuntu 8.04 as my test system. I'll install 9.04 in a VM tomorrow and see if it changes anything. 
No need, I have fixed this at last.

Error was in code chunk, I was reffering to earlier, macro INPUT_SDL_JOYSTICK_CHECK_POVHAT_DIRECTION, see patch for further info.

Though, can't say anything POVHAT, SDL seems to support it on Linux.
Now everything is working correctly.

---

### Post by GerbilSoft on 2009-08-16
> **superG said:**
> No need, I have fixed this at last.

Error was in code chunk, I was reffering to earlier, macro INPUT_SDL_JOYSTICK_CHECK_POVHAT_DIRECTION, see patch for further info.

Though, can't say anything POVHAT, SDL seems to support it on Linux.
Now everything is working correctly.
Bah, it's the fact that SDL's POV hat structure is a bitfield and not a single number. Thanks for narrowing this down. I have applied the patch.

I'm still going to test out Ubuntu 9.04 in a VM anyway, because I'm thinking Ubuntu decided to apply a patch to SDL to map axes 6 and 7 to a POV hat for some reason.

EDIT: Just tested it, and Ubuntu 9.04 does map my GameCube controller's D-pad to POV. It doesn't look like they added any specific patches to SDL with regards to POV, so I can't figure out exactly what changed it. Either way, it works now.

---

### Post by x-demon on 2009-08-23
Is kaillera support planned? Since it's de-facto netplay in emulators... There is open kaillera client, why not use it's codebase?

---

### Post by GerbilSoft on 2009-09-12
Yet another preview release, r7_pre4. This has the POV hat fix as well as a fix for an SRAM regression that broke some games that use SRAM.

> **x-demon said:**
> Is kaillera support planned? Since it's de-facto netplay in emulators... There is open kaillera client, why not use it's codebase?
I am planning on adding netplay support eventually, but I probably won't use Kaillera. I've had plenty of issues with Kaillera before, including the fact that it uses filenames to match ROM images instead of CRC32 or MD5. Also, the closed library has plenty of security holes, and I'm pretty sure that, on the Windows side at least, people will insist on using the Win32 Kaillera client library and server program, which will result in massive security holes.

---

### Post by GerbilSoft on 2009-10-11
Gens/GS r7_pre5 is out. Hopefully, this will be the last preview release before r7 final. Links are in the first post.

---

### Post by disturbedite on 2009-10-11
@ GerbilSoft

thanks for continuing development on a great emulator & making it even better.

i also wanted to say thanks for keeping a detailed yet easy to read/follow changelog.

---

### Post by BigSilly on 2009-10-12
Just wanted to post up too to say thanks for a great emulator and your continued work on it. Bring on the final release! :D

Thanks again.

---

### Post by ezekiel000 on 2010-08-24
Will Mega Mouse support be added in the future? (Or is it already supported and I missed it)

I just got Urusei Yatsura My Dear Friends in the mail and noticed it can use the mega mouse, being a point and click adventure using a mouse would be preferable to a joypad.

---

### Post by GerbilSoft on 2010-08-24
> **ezekiel000 said:**
> Will Mega Mouse support be added in the future? (Or is it already supported and I missed it)

I just got Urusei Yatsura My Dear Friends in the mail and noticed it can use the mega mouse, being a point and click adventure using a mouse would be preferable to a joypad.
There is initial Mega Mouse support in the upcoming Gens/GS II. I haven't figured out how to reliably detect relative mouse movement using Qt yet, so only mouse buttons work right now.

---

### Post by ezekiel000 on 2010-08-24
That's good to hear. I didn't know there was a Qt front end I thought it was only GTK.

I'm not a programmer but this might help:
[http://www.weask.us/entry/grab-mouse-movement](http://www.weask.us/entry/grab-mouse-movement)

---

### Post by GerbilSoft on 2010-08-24
> **ezekiel000 said:**
> That's good to hear. I didn't know there was a Qt front end I thought it was only GTK.

I'm not a programmer but this might help:
[http://www.weask.us/entry/grab-mouse-movement](http://www.weask.us/entry/grab-mouse-movement)
Gens/GS II is a partial rewrite of Gens/GS that I started a few months ago. Among other things, the emulation code is now completely separate from the UI, and I'm using Qt for the UI on Linux, Windows, and Mac OS X.

Some other notable stuff include a C++ VDP rewrite (started for Gens/GS r7.1, but moved to Gens/GS II), a new savestate format "ZOMG" (in development), and a controller subsystem rewrite. For controllers, I'm also improving the input subsystem to allow the use of multiple keyboards (WM_INPUT on Windows, MPX on linux) and Wii Remotes (cwiid on Linux; not sure if I'll implement this on Windows).

I've tried the various stuff mentioned on that page regarding mouse movement, but I decided to concentrate on the more important stuff for now.

---

### Post by JMMR on 2010-10-19
I was wondering if there is a hash (md5sum &/or sha1sum) for all of the downloads.  Just to help ensure that the file being downloaded is legit, it makes it easy to check.

---

### Post by GerbilSoft on 2010-10-21
> **JMMR said:**
> I was wondering if there is a hash (md5sum &/or sha1sum) for all of the downloads.  Just to help ensure that the file being downloaded is legit, it makes it easy to check.

Here's the md5sums and sha1sums of the current packages.

gens-gs-r7.tar.gz:
md5sum: bcb17b49774aa318a224c741028aabc3
sha1sum: a7c882813b57f7448947619c1cabfa7ede685b7a

gens_2.16.7_i386.deb:
md5sum: ac71f00e5c1de21360c12d370c3d8a8c
sha1sum: 420ff8019f30a865ac76dd776068bbc909e89e9c

gens-gs-r7-win32-pkg1.zip:
md5sum: ed00937da6bc75f8e02696dcff6fa41d
sha1sum: 621915f2d5a9b777efaf105e69e10af189ae5fc1

---

### Post by andlinux on 2011-03-05
I installed Gens-gs-r7 on my HTPC that's running XMBC live (Dharma), in the past I used also Kega Fusion and the older Gens (2.15). Now I was thinking by myself what if this new version has an option to quit Gens with the gamepad, by pressing on an assigned button. So I compiled it for my htpc and installed it.

But I was wrong, there's still no option to do that, Zsnes has that option and it's very handy.

So my question is, when can we expect such an option ?

---

### Post by GerbilSoft on 2011-03-07
As mentioned previously, I'm working on a partial rewrite of Gens/GS called Gens/GS II. One of the features I implemented recently is the ability to remap hotkeys for menu actions such as Quit. Currently, it's still limited to one key per action, but I plan on expanding it to allow multiple keys for a given action after the first preview release.

The first preview release will not support gamepads, but this will be added for the second preview release. Gamepad buttons will be assignable as hotkeys, so you'll be able to map gamepad buttons for quit, savestate, loadstate, etc.

(Also, I'm planning on adding special Linux-only support for Wii remotes using libcwiid. :))

---

### Post by andlinux on 2011-03-07
Oops my mistake, 
I didn't see that you are working on a rewrite of Gens/GS.
If you want a translation to Dutch just let me know, 
that's probably all that I can do to help.

One last thing I wanted to know. 
When can we expect Gens/GS II ?

---

### Post by GerbilSoft on 2011-03-07
> **andlinux said:**
> One last thing I wanted to know. 
When can we expect Gens/GS II ?

I'm not committing to any release dates, so "when it's ready".

I'm currently waiting for someone else to help me out with the framedropping code, which is the major blocker for a release. The first release, 1.0_pre1, will only have Genesis emulation and won't have gamepad support. 1.0_pre2 will have Sega CD and gamepad support, and 1.0_pre3 will have 32X.

Also, thanks for the translation offer. Strings aren't frozen yet, so I'm not accepting any more translations at the moment. I'll post a topic on Sonic Retro's Gens/GS subforum once I freeze strings.

---

### Post by Shazzner on 2011-03-07
I'm getting a compile error from that latest source:
```
i/gtk/gens/.deps/gens-gens_window_callbacks.Tpo -c -o ui/gtk/gens/gens-gens_window_callbacks.o `test -f 'ui/gtk/gens/gens_window_callbacks.cpp' || echo './'`ui/gtk/gens/gens_window_callbacks.cpp
ui/gtk/gens/gens_window_callbacks.cpp: In function ‘gboolean gens_window_drag_drop(GtkWidget*, GdkDragContext*, gint, gint, guint, void*)’:
ui/gtk/gens/gens_window_callbacks.cpp:157: error: ‘struct _GdkDragContext’ has no member named ‘targets’
ui/gtk/gens/gens_window_callbacks.cpp:159: error: ‘struct _GdkDragContext’ has no member named ‘targets’
ui/gtk/gens/gens_window_callbacks.cpp: At global scope:
ui/gtk/gens/gens_window_callbacks.cpp:243: warning: unused parameter ‘user_data’
make[4]: *** [ui/gtk/gens/gens-gens_window_callbacks.o] Error 1

```
Any idea on this? Thanks

---

### Post by GerbilSoft on 2011-03-07
> **Shazzner said:**
> I'm getting a compile error from that latest source:
```
i/gtk/gens/.deps/gens-gens_window_callbacks.Tpo -c -o ui/gtk/gens/gens-gens_window_callbacks.o `test -f 'ui/gtk/gens/gens_window_callbacks.cpp' || echo './'`ui/gtk/gens/gens_window_callbacks.cpp
ui/gtk/gens/gens_window_callbacks.cpp: In function &#8216;gboolean gens_window_drag_drop(GtkWidget*, GdkDragContext*, gint, gint, guint, void*)&#8217;:
ui/gtk/gens/gens_window_callbacks.cpp:157: error: &#8216;struct _GdkDragContext&#8217; has no member named &#8216;targets&#8217;
ui/gtk/gens/gens_window_callbacks.cpp:159: error: &#8216;struct _GdkDragContext&#8217; has no member named &#8216;targets&#8217;
ui/gtk/gens/gens_window_callbacks.cpp: At global scope:
ui/gtk/gens/gens_window_callbacks.cpp:243: warning: unused parameter &#8216;user_data&#8217;
make[4]: *** [ui/gtk/gens/gens-gens_window_callbacks.o] Error 1

```
Any idea on this? Thanks
The problem is GTK+'s documentation recommended setting options to disable deprecated functionality, so I did that; then they deprecated more functions.

A workaround is to remove line 214 from configure.ac:
```
GTK_CFLAGS="$GTK_CFLAGS -DGTK_DISABLE_DEPRECATED -DDISABLE_DEPRECATED -DGSEAL_ENABLE"
```

then run autoreconf and rerun configure.

---

### Post by Shazzner on 2011-03-08
> **GerbilSoft said:**
> The problem is GTK+'s documentation recommended setting options to disable deprecated functionality, so I did that; then they deprecated more functions.

A workaround is to remove line 214 from configure.ac:
```
GTK_CFLAGS="$GTK_CFLAGS -DGTK_DISABLE_DEPRECATED -DDISABLE_DEPRECATED -DGSEAL_ENABLE"
```

then run autoreconf and rerun configure.

Got it, thanks for the reply!

Time to play some Shadowrun :)

---

### Post by muzikayise on 2012-01-14
> **BigSilly said:**
> I actually created a .deb for 64 bit using a script I got off the World of Goo forums! Don't ask me how it works, it just does. :D I've attached it anyway, and I'll add another post with the script I got.

Hope this helps anyway.

thanks buddy this works perfect on ubuntu 11.10

busy playing Dune: The Battle For Arrakis, this game is a classic.

thanks again

---

### Post by BigSilly on 2012-01-14
> **muzikayise said:**
> thanks buddy this works perfect on ubuntu 11.10

busy playing Dune: The Battle For Arrakis, this game is a classic.

thanks again

It still works?? :o

Cool!

Have you tried [Kega Fusion on Linux]("http://www.eidolons-inn.net/tiki-download_file.php?fileId=572") too? Works very well imho. Still, I hope development is still ongoing for this, though I sadly expect not. :(

---

### Post by ROKERA on 2012-03-10
Good afternoon. I write with the help of Google translator. I am from Russia. The problem is this: when a game console emulator Gens\gs is open to full screen, it does not work hotkey ALT + F4. If the emulator is running in windowed mode, the hot keys work fine.
 Operating system - Ubuntu 10.04.3 LTS

---

### Post by Yrralhann on 2012-12-20
Thanks, this script works perfectly, probably works with other i386 packages you're having trouble installing also. The lack of an i386 version of xdg-utils seems to be what's causing the issue...... this script magically fixes it.... where dkpg --force-architecture wont.... which is kinda wierd really. o.O

the easiest way to use this script is copy it and the Gens_2.16.7_i386.deb package into the same folder, open a terminal in that folder and use the following command line

```
./deb-from-i386-to-amd64.sh Gens_2.16.7_i386.deb Gens_2.16.7_amd64.deb
```> **BigSilly said:**
> Here's the 32 to 64 bit .deb script. It's quite easy to use. :)  I'm no Linux expert at all, but this worked for me anyway.

EDIT: Sorry, rude of me. Here's the Read Me.

Attached is a shell script to convert the 32-bit Debian packages to 64-bit packages, if you prefer those. Unpack, mark executable, and run on the command line with the path to the 32-bit package as an argument. Like so:

username@username-desktop:~$ '/home/username/Downloads/deb-from-i386-to-amd64.sh'  '/home/username/Emulators/Gens_2.15.5-gs-m6-1_i386.deb'  Gens_2.15.5-gs-m6-1_amd64.deb

Obviously substitute the package there with whichever emulator or package you are wanting to use.

---

