---
title: "Trying to run ut2003"
date: 2006-04-30
forum: Gaming &amp; Leisure
---

### Post by jc87 on 2006-04-30
I installed UT2003 at Ubuntu (Dapper Drake , i´m posting here because there  is no gaming section for Dapper , yet!).

My problem is that when i try to run the game  , it appers the UT2003 logo image , the screen goes black for a few seconds , but then it goes back to Gnome .

I runned the starter at the gnome-terminal , this is the output : 

```

jc87@ubuntu:~/ut2003$ sh ut2003
open /dev/dsp: Device or resource busy
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

Backtrace:
[ 1]  ./Core.so [0xb74c9c32]
[ 2]  [0xffffe420]
[ 3]  /usr/lib/dri/atiogl_a_dri.so(__R200TCLProcessArrayPrimitive+0x162) [0xb3d0 33b2]
[ 4]  /usr/lib/dri/atiogl_a_dri.so(__glim_R200TCLDrawArrays+0xb6f) [0xb3d3ef5f]
[ 5]  /usr/lib/dri/atiogl_a_dri.so(__glim_R200TCLDrawArrays+0xdfe) [0xb3d3f1ee]
[ 6]  /home/jc87/ut2003/System/OpenGLDrv.so(DrawPrimitive__22FOpenGLRenderInterf ace14EPrimitiveTypeiiii+0x348) [0xb477a5b0]
[ 7]  ./Engine.so(Flush__11FCanvasUtil+0x1dc) [0xb78524fc]
[ 8]  ./Engine.so(_._11FCanvasUtil+0x28) [0xb785223c]
[ 9]  ./Engine.so(Render__16FPlayerSceneNodeP16FRenderInterface+0x97a) [0xb78438 b6]
[10]  ./Engine.so(Draw__11UGameEngineP9UViewportiPUcPi+0x3f8) [0xb777f63c]
[11]  /home/jc87/ut2003/System/SDLDrv.so(Repaint__12USDLViewporti+0x33) [0xb47a1 86b]
[12]  /home/jc87/ut2003/System/SDLDrv.so(Tick__10USDLClient+0x83) [0xb47a029b]
[13]  ./Engine.so(Tick__11UGameEnginef+0x32d8) [0xb77867f8]
[14]  ./ut2003-bin(SDL_SetVideoMode+0x965) [0x8051a3d]
[15]  ./ut2003-bin(main+0x328c) [0x8058a5c]
[16]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb72bbea2]
[17]  ./ut2003-bin(ValidateCDKey__Fv+0x49) [0x80511f1]
Signal: SIGSEGV [segmentation fault]
Aborting.

```

My GPU is an Ati Radeon 9250 with fglrx drivers (from the official repo) , anyone knows what may be causing the problem?

Edit : By the way , is installed at /home/jc87/ut2003 (i don´t know if that helps).

---

### Post by Adrian_b on 2006-04-30
It works fine here.. (Got the demo from a 'Linux Magazine' cd)
Although i have NVidia drivers.
But i don't know what segmentation faults actually mean, i've seen them happen, and be fixed a few times afterwards :s

---

### Post by Jason_25 on 2006-04-30
Have you tried the demo?  It looks like your trying to run the full game.  Notice it seems to fail at the cd check.

---

### Post by collitis on 2007-08-23
I get the same "XiG-SUNDRY-NONSTANDARD" error message when I run the game from the terminal window, and it runs fine. suggest you look at ~/ut2003/System/cdkey and see if your cdkey is in there, if not, manually enter it in AAAAA-BBBBB-CCCCC-DDDDD format.

EDIT:  As soon as I posted this message, UT2003 started crashing on me and spitting out that segmentation fault after running the game for about 15-20 minutes. Would also appreciate assistance on this.

---

