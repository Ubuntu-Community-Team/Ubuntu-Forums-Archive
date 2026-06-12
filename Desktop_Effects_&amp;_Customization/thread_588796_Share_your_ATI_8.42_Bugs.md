---
title: "Share your ATI 8.42 Bugs"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by superyounan1 on 2007-10-23
So heres what i get:

I tried both
[http://ubuntuforums.org/showthread.php?t=588605]("http://ubuntuforums.org/showthread.php?t=588605")
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

modifying the instructions in the second link as needed for the new driver and gutsy, here are the results:


```
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6958 Release



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6958 Release

*** glibc detected *** fglrxinfo: double free or corruption (!prev): 0x08062060 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d2bd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d2f800]
/usr/lib/dri/fglrx_dri.so[0xb79d6c92]
/usr/lib/libGL.so.1[0xb7f3ac61]
/usr/lib/libX11.so.6(_XFreeExtData+0x25)[0xb7e397d5]
/usr/lib/libX11.so.6(_XFreeDisplayStructure+0x2f6)[0xb7e45df6]
/usr/lib/libX11.so.6(XCloseDisplay+0xea)[0xb7e32eea]
fglrxinfo[0x8048a3b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cd8050]
fglrxinfo[0x80488f1]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 03:42 1590715    /usr/bin/fglrxinfo
0804b000-0804c000 rw-p 00002000 03:42 1590715    /usr/bin/fglrxinfo
0804c000-08475000 rw-p 0804c000 00:00 0          [heap]
a5fc9000-a5fca000 rw-p a5fc9000 00:00 0 
a628c000-ae28c000 rw-s 00003000 00:0e 19424      /dev/dri/card0
ae28c000-ae54e000 rw-p ae28c000 00:00 0 
ae54e000-ae554000 rwxp ae54e000 00:00 0 
ae554000-ae5c7000 rw-p ae554000 00:00 0 
ae5c7000-aecc7000 rw-s 00005000 00:0e 19424      /dev/dri/card0
aecc7000-aecd7000 rw-s 00004000 00:0e 19424      /dev/dri/card0
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6cbd000-b6cc7000 r-xp 00000000 03:42 491587     /lib/libgcc_s.so.1
b6cc7000-b6cc8000 rw-p 0000a000 03:42 491587     /lib/libgcc_s.so.1
b6cd7000-b6cfa000 r-xp 00000000 03:42 525587     /lib/tls/i686/cmov/libm-2.6.1.so
b6cfa000-b6cfc000 rw-p 00023000 03:42 525587     /lib/tls/i686/cmov/libm-2.6.1.so
b6cfc000-b6d03000 r-xp 00000000 03:42 525609     /lib/tls/i686/cmov/librt-2.6.1.so
b6d03000-b6d05000 rw-p 00006000 03:42 525609     /lib/tls/i686/cmov/librt-2.6.1.so
b6d05000-b7abe000 r-xp 00000000 03:42 4161553    /usr/lib/dri/fglrx_dri.so
b7abe000-b7b43000 rw-p 00db9000 03:42 4161553    /usr/lib/dri/fglrx_dri.so
b7b43000-b7c9d000 rw-p b7b43000 00:00 0 
b7c9d000-b7c9f000 r-xp 00000000 03:42 525585     /lib/tls/i686/cmov/libdl-2.6.1.so
b7c9f000-b7ca1000 rw-p 00001000 03:42 525585     /lib/tls/i686/cmov/libdl-2.6.1.so
b7ca1000-b7ca5000 r-xp 00000000 03:42 1590579    /usr/lib/libXdmcp.so.6.0.0
b7ca5000-b7ca6000 rw-p 00003000 03:42 1590579    /usr/lib/libXdmcp.so.6.0.0
b7ca6000-b7ca7000 rw-p b7ca6000 00:00 0 
b7ca7000-b7ca9000 r-xp 00000000 03:42 1590568    /usr/lib/libXau.so.6.0.0
b7ca9000-b7caa000 rw-p 00001000 03:42 1590568    /usr/lib/libXau.so.6.0.0
b7caa000-b7cbe000 r-xp 00000000 03:42 525605     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7cbe000-b7cc0000 rw-p 00013000 03:42 525605     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7cc0000-b7cc2000 rw-p b7cc0000 00:00 0 
b7cc2000-b7e06000 r-xp 00000000 03:42 525579     /lib/tls/i686/cmov/libc-2.6.1.so
b7e06000-b7e07000 r--p 00143000 03:42 525579     /lib/tls/i686/cmov/libc-2.6.1.so
b7e07000-b7e09000 rw-p 00144000 03:42 525579     /lib/tls/i686/cmov/libc-2.6.1.so
b7e09000-b7e0c000 rw-p b7e09000 00:00 0 
b7e0c000-b7e19000 r-xp 00000000 03:42 1590583    /usr/lib/libXext.so.6.4.0
b7e19000-b7e1a000 rw-p 0000d000 03:42 1590583    /usr/lib/libXext.so.6.4.0
b7e1a000-b7f07000 r-xp 00000000 03:42 1590562    /usr/lib/libX11.so.6.2.0
b7f07000-b7f0b000 rw-p 000ed000 03:42 1590562    /usr/lib/libX11.so.6.2.0
b7f0b000-b7f91000 r-xp 00000000 03:42 901295     /usr/lib/xorg/libGL.so.1.2
b7f91000-b7f93000 rw-p 00086000 03:42 901295     /usr/lib/xorg/libGL.so.1.2
b7f93000-b7f96000 rw-p b7f93000 00:00 0 
b7fa1000-b7fa3000 rw-s 00002000 00:0e 19424      /dev/dri/card0
b7fa5000-b7fa6000 rw-p b7fa5000 00:00 0 
b7fa6000-b7fc0000 r-xp 00000000 03:42 491540     /lib/ld-2.6.1.so
b7fc0000-b7fc2000 rw-p 00019000 03:42 491540     /lib/ld-2.6.1.so
bfbb8000-bfbcd000 rwxp bfbb8000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

glxgears performs better than before, about 7100 fps, but when i stop it, i get a similar outptu as above, and off course compiz doesn't load.

---

### Post by beaveyOne on 2007-10-24
I have the exact same problem.  Anyone know how to fix this?

This error crops up anytime I run something that hits the 3d:

***** glibc detected *** *app*: double free or corruption (top): 0x08912eb0 *****

(*app* will always be the name of whatever app was running).  It's usually followed by a backtrace.  This is frustrating.

---

### Post by rbmorse on 2007-10-24
The driver loads for me, and Compiz works fine, but video playback with Xv selected is very choppy.  X11 works.  Some embedded video from streaming web sites does not play at all.

---

### Post by Trevster on 2007-10-24
I get the same error. Not sure what to try next. I used the steps in post #3 here: [HTML]http://ubuntuforums.org/showthread.php?t=589637[/HTML]



```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

*** glibc detected *** fglrxinfo: double free or corruption (!prev): 0x08062060 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cbbd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7cbf800]
/usr/lib/dri/fglrx_dri.so[0xb7966c92]
/usr/lib/libGL.so.1[0xb7ecbc61]
/usr/lib/libX11.so.6(_XFreeExtData+0x25)[0xb7dca7d5]
/usr/lib/libX11.so.6(_XFreeDisplayStructure+0x2f6)[0xb7dd6df6]
/usr/lib/libX11.so.6(XCloseDisplay+0xea)[0xb7dc3eea]
fglrxinfo[0x8048a3b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c68050]
fglrxinfo[0x80488f1]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:11 3884981    /usr/bin/fglrxinfo
0804b000-0804c000 rw-p 00002000 08:11 3884981    /usr/bin/fglrxinfo
0804c000-088f3000 rw-p 0804c000 00:00 0          [heap]
a587e000-a587f000 rw-p a587e000 00:00 0 
a5e99000-a5e9b000 rw-s 00002000 00:0e 18191      /dev/dri/card0
a5e9b000-ade9b000 rw-s 00003000 00:0e 18191      /dev/dri/card0
ade9b000-ae15d000 rw-p ade9b000 00:00 0 
ae15d000-ae163000 rwxp ae15d000 00:00 0 
ae163000-ae4de000 rw-p ae163000 00:00 0 
ae4de000-ae4e4000 rwxp ae4de000 00:00 0 
ae4e4000-ae557000 rw-p ae4e4000 00:00 0 
ae557000-aec57000 rw-s 00005000 00:0e 18191      /dev/dri/card0
aec57000-aec67000 rw-s 00004000 00:0e 18191      /dev/dri/card0
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6c5c000-b6c66000 r-xp 00000000 08:11 4161558    /lib/libgcc_s.so.1
b6c66000-b6c67000 rw-p 0000a000 08:11 4161558    /lib/libgcc_s.so.1
b6c67000-b6c8a000 r-xp 00000000 08:11 4195245    /lib/tls/i686/cmov/libm-2.6.1.so
b6c8a000-b6c8c000 rw-p 00023000 08:11 4195245    /lib/tls/i686/cmov/libm-2.6.1.so
b6c8c000-b6c93000 r-xp 00000000 08:11 4195257    /lib/tls/i686/cmov/librt-2.6.1.so
b6c93000-b6c95000 rw-p 00006000 08:11 4195257    /lib/tls/i686/cmov/librt-2.6.1.so
b6c95000-b7a4e000 r-xp 00000000 08:11 6180097    /usr/lib/dri/fglrx_dri.so
b7a4e000-b7ad3000 rw-p 00db9000 08:11 6180097    /usr/lib/dri/fglrx_dri.so
b7ad3000-b7c2e000 rw-p b7ad3000 00:00 0 
b7c2e000-b7c30000 r-xp 00000000 08:11 4195244    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c30000-b7c32000 rw-p 00001000 08:11 4195244    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c32000-b7c36000 r-xp 00000000 08:11 3884326    /usr/lib/libXdmcp.so.6.0.0
b7c36000-b7c37000 rw-p 00003000 08:11 3884326    /usr/lib/libXdmcp.so.6.0.0
b7c37000-b7c39000 r-xp 00000000 08:11 3884315    /usr/lib/libXau.so.6.0.0
b7c39000-b7c3a000 rw-p 00001000 08:11 3884315    /usr/lib/libXau.so.6.0.0
b7c3a000-b7c4e000 r-xp 00000000 08:11 4195255    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7c4e000-b7c50000 rw-p 00013000 08:11 4195255    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7c50000-b7c52000 rw-p b7c50000 00:00 0 
b7c52000-b7d96000 r-xp 00000000 08:11 4195241    /lib/tls/i686/cmov/libc-2.6.1.so
b7d96000-b7d97000 r--p 00143000 08:11 4195241    /lib/tls/i686/cmov/libc-2.6.1.so
b7d97000-b7d99000 rw-p 00144000 08:11 4195241    /lib/tls/i686/cmov/libc-2.6.1.so
b7d99000-b7d9c000 rw-p b7d99000 00:00 0 
b7d9c000-b7da9000 r-xp 00000000 08:11 3884330    /usr/lib/libXext.so.6.4.0
b7da9000-b7daa000 rw-p 0000d000 08:11 3884330    /usr/lib/libXext.so.6.4.0
b7daa000-b7dab000 rw-p b7daa000 00:00 0 
b7dab000-b7e98000 r-xp 00000000 08:11 3884516    /usr/lib/libX11.so.6.2.0
b7e98000-b7e9c000 rw-p 000ed000 08:11 3884516    /usr/lib/libX11.so.6.2.0
b7e9c000-b7f22000 r-xp 00000000 08:11 3884979    /usr/lib/libGL.so.1.2
b7f22000-b7f24000 rw-p 00086000 08:11 3884979    /usr/lib/libGL.so.1.2
b7f24000-b7f26000 rw-p b7f24000 00:00 0 
b7f36000-b7f38000 rw-p b7f36000 00:00 0 
b7f38000-b7f52000 r-xp 00000000 08:11 4161549    /lib/ld-2.6.1.so
b7f52000-b7f54000 rw-p 00019000 08:11 4161549    /lib/ld-2.6.1.so
bfeda000-bfeee000 rwxp bfeda000 00:00 0          [stack]
bfeee000-bfeef000 rw-p bfeee000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

---

### Post by superyounan1 on 2007-10-24
I found out a little more about this bug, turns out it is very typical in Dual-Head configurations, you guys using dual-head / tv-out?

Its tricky, but if you switch to single-head AIGLX should load and compiz will load

I managed to it going, but I was disappointed with the performance. XGL with older drivers was more stable and smoother, and so is the open driver with AIGLX. And off course you have to sacrifice dual-head. 

Its a good first step, very belated and still very buggy, but better late than never. For now I'm back to 8.40 with dual-head, and just forgetting about compiz, its the most stable setup i can do with my card

---

### Post by Trevster on 2007-10-24
Thanks for the information.  I am kinda addicted to the dual monitors so I will live without compiz for now.

---

### Post by beaveyOne on 2007-10-24
Yep, I just verified that the problem occurs only with dual-head.  Unplugged my external monitor from my laptop, and I have no more errors.  AIGLX and Compiz work perfectly, too.  I guess I'll just live without the effects until ATI releases a driver that works with dual-head.

One thing I noticed, though, is that performance with just the single screen is great with AIGLX on my machine.  I don't have any of the problems described in this thread.  No slowness or anything.  Weird.

---

### Post by Melcar on 2007-10-25
Mouse scrolling is slow, a lot of screen tearing (mostly when I'm scrolling web pages), and no video playback when Compiz effects are enabled.

---

### Post by superyounan1 on 2007-10-25
> **Melcar said:**
> Mouse scrolling is slow, a lot of screen tearing (mostly when I'm scrolling web pages), and no video playback when Compiz effects are enabled.

yeah me too, it must depend on the chipset, my card has R350 (9800 pro). I also get artifacts on the screen, low fps, random hiccups, and the computer freezes on X is restarted. Overall theres mroe good than bad, but I just couldn't live with it, i'd rather have no effects. 

for me, might be 2 or 3 more months before its mature enough to get me to switch, thats assuming they're still dedicated to supporting my 4 year old card

---

### Post by dark_harmonics on 2007-10-25
I can also report the dual-head failure on two computers. One has a radeon 9600 and another is an X1600 (MBP). Anybody with a solution? Or is everybody just giving up...

**Edit** I gave up as well after toying with getting it to work for 4 hours or so. Hopefully the next driver will offer better support for the dual-head configuration :(

---

### Post by voided3 on 2007-10-25
Running Gutsy and an x1300pro; screen brightness doesn't change or be affected by game setting for most full screen games. I also get strange lines in the lower right hand corner of my screen after a while that look like dead LCD pixels... Oh, and enabling desktop effects doesn't work, but the compositor on Xubuntu worked.

---

### Post by Melcar on 2007-10-25
> **voided3 said:**
> Running Gutsy and an x1300pro; screen brightness doesn't change or be affected by game setting for most full screen games. I also get strange lines in the lower right hand corner of my screen after a while that look like dead LCD pixels... Oh, and enabling desktop effects doesn't work, but the compositor on Xubuntu worked.


Did you "whitelist" fglrx?  You also have to remove your GPU from the blacklist if it happens to be there.   Look in  /usr/bin/compiz

---

### Post by murlosad on 2007-10-26
> **rbmorse said:**
> The driver loads for me, and Compiz works fine, but video playback with Xv selected is very choppy.  X11 works.  Some embedded video from streaming web sites does not play at all.

I'm having a lot of the same problems, mostly with video playback. VLC is basically useless even using X11 for playback, mplayer works ok with xv but I can't change the size of the video which is annoying at best. has anyone come up with a workaround for these problems yet?

---

### Post by Mike Maximus on 2007-10-26
> **murlosad said:**
> I'm having a lot of the same problems, mostly with video playback. VLC is basically useless even using X11 for playback, mplayer works ok with xv but I can't change the size of the video which is annoying at best. has anyone come up with a workaround for these problems yet?

Same problems here.  Video flickers badly,  and if I change to X11 or any other output that works CPU usage will skyrocket and the video chops anyway.  I've just been turning compiz off if I need to watch dvd or any video that requires full-screen.

Also any OpenGL application (Google Earth, etc) that runs in a window flickers like hell, which you get around sort of by using the toggle redirect or toggle fullscreen shortcuts in compiz.  Which you can find under "Extra WM Actions" in the compiz manager.

A high note is that ET: Quake Wars seems to run very well, now I don't have to boot to XP to play it.

:guitar:

---

### Post by cybrid on 2007-10-26
> **murlosad said:**
> I'm having a lot of the same problems, mostly with video playback. VLC is basically useless even using X11 for playback, mplayer works ok with xv but I can't change the size of the video which is annoying at best. has anyone come up with a workaround for these problems yet?

Im in the same situation, my card is an old 9600XT. I supouse our expectations were too high on a new driver. Maybe for 8.04.

P.S: Don't you just feel you hear that "maybe in the next....." phrase too much ;) .

---

### Post by Eviltelm on 2007-10-27
It works almost very good to me, even compiz-fusion is faster, the almost part is because of the scroll issue :( but it only works badly when compiz is on, if i disable it everything works great! maybe the problem can be solved in the next driver (or compiz)

EDIT: ati mobility X1400 :)
EDIT2: yes, i forgot the video issue lol, but i think this problem us gutsy's because with the 8.37 or older video with feisty worked fine when in xgl and now not in xgl or aiglx

---

### Post by NoVista on 2007-10-27
If your card isn't FULLY supported by these drivers, it is not a bug.

---

### Post by miggols99 on 2007-10-27
I'm running the ATI 8.42 driver in Arch Linux. Generally everything feels faster, games have higher FPS and glxgears gets a high increase. The only problem I have is Compiz Fusion. It doesn't work. When I do fusion-icon I get a white screen and the only thing I can do is restart X.

---

