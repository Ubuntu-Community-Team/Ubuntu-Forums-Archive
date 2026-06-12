---
title: "directfb enabling"
date: 2009-01-08
forum: General Help
---

### Post by oguzy on 2009-01-08
Hi,

I am trying to run some of the applications by using DirectFB. After
googling a bit i enabled the framebuffer property at my Ubuntu Hardy.
Here is the fbset and dfblayer outputs

# fbset -i

mode "1280x1024-77"
   # D: 131.096 MHz, H: 80.328 kHz, V: 76.649 Hz
   geometry 1280 1024 1280 1024 32
   timings 7628 160 32 16 4 160 4
   rgba 8/16,8/8,8/0,8/24
endmode

Frame buffer device information:
   Name        : VESA VGA
   Address     : 0xc0000000
   Size        : 8060928
   Type        : PACKED PIXELS
   Visual      : TRUECOLOR
   XPanStep    : 0
   YPanStep    : 0
   YWrapStep   : 0
   LineLength  : 5120
   Accelerator : No

# dfblayer

    =======================|  DirectFB 1.0.1  |=======================
         (c) 2001-2007  The DirectFB Organization (directfb.org)
         (c) 2000-2004  Convergence (integrated media) GmbH
       ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15)

(*) Direct/Thread: Running 'VT Switcher' (CRITICAL, 8193)...


(*) Direct/Thread: Running 'Linux Input' (INPUT, 8196)...
(*) DirectFB/Input: Macintosh mouse button emulatio (1) 0.1 (directfb.org)

(*) Direct/Thread: Running 'Linux Input' (INPUT, 8197)...
(*) DirectFB/Input: AT Translated Set 2 keyboard (2) 0.1 (directfb.org)

(*) Direct/Thread: Running 'Linux Input' (INPUT, 8198)...
(*) DirectFB/Input: PC Speaker (3) 0.1 (directfb.org)

(*) Direct/Thread: Running 'Linux Input' (INPUT, 8199)...
(*) DirectFB/Input: Power Button (FF) (4) 0.1 (directfb.org)

(*) Direct/Thread: Running 'Linux Input' (INPUT, 8200)...
(*) DirectFB/Input: Power Button (CM) (5) 0.1 (directfb.org)

(*) Direct/Thread: Running 'Linux Input' (INPUT, 8201)...
(*) DirectFB/Input: ImPS/2 Generic Wheel Mouse (6) 0.1 (directfb.org)
(*) Direct/Thread: Running 'Keyboard Input' (INPUT, 8202)...
(*) DirectFB/Input: Keyboard 0.9 (directfb.org)

(*) Direct/Thread: Running 'PS/2 Input' (INPUT, 8203)...

(*) DirectFB/Input: IMPS/2 Mouse 1.0 (directfb.org)
(*) DirectFB/Genefx: MMX detected and enabled
(*) DirectFB/Graphics: MMX Software Rasterizer 0.6 (directfb.org)
(*) DirectFB/Core/WM: Default 0.3 (directfb.org)
(!) DirectFB/FBDev: Panning display failed (x=0 y=0 ywrap=0 vbl=0)!
   --> Invalid argument

FBDev Primary Layer

Width       640
Height      480
Format      RGB32
Buffermode  BACKSYSTEM


I can set the frame layer by using dfblayer -m also. To test the
directfb issue, i change to another virtual konsole and stopped the
gdm so that no X will be running.

I ran links2 first.
# links2 -driver directfb

    =======================|  DirectFB 1.0.1  |=======================
         (c) 2001-2007  The DirectFB Organization (directfb.org)
         (c) 2000-2004  Convergence (integrated media) GmbH
       ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15)
(*) Direct/Thread: Running 'VT Switcher' (CRITICAL, 6641)...
(*) Direct/Thread: Running 'Linux Input' (INPUT, 6644)...
(*) DirectFB/Input: Macintosh mouse button emulatio (1) 0.1 (directfb.org)
(*) Direct/Thread: Running 'Linux Input' (INPUT, 6645)...
(*) DirectFB/Input: AT Translated Set 2 keyboard (2) 0.1 (directfb.org)
(*) Direct/Thread: Running 'Linux Input' (INPUT, 6646)...
(*) DirectFB/Input: Power Button (FF) (3) 0.1 (directfb.org)
(*) Direct/Thread: Running 'Linux Input' (INPUT, 6647)...
(*) DirectFB/Input: Power Button (CM) (4) 0.1 (directfb.org)
(*) Direct/Thread: Running 'Linux Input' (INPUT, 6648)...
(*) DirectFB/Input: PC Speaker (5) 0.1 (directfb.org)
(*) Direct/Thread: Running 'Linux Input' (INPUT, 6649)...
(*) DirectFB/Input: ImPS/2 Generic Wheel Mouse (6) 0.1 (directfb.org)
(*) Direct/Thread: Running 'Keyboard Input' (INPUT, 6650)...
(*) DirectFB/Input: Keyboard 0.9 (directfb.org)
(*) Direct/Thread: Running 'PS/2 Input' (INPUT, 6651)...
(*) DirectFB/Input: IMPS/2 Mouse 1.0 (directfb.org)
(*) DirectFB/Genefx: MMX detected and enabled
(*) DirectFB/Graphics: MMX Software Rasterizer 0.6 (directfb.org)
(*) DirectFB/Core/WM: Default 0.3 (directfb.org)
(!) DirectFB/FBDev: Panning display failed (x=0 y=0 ywrap=0 vbl=0)!
   --> Invalid argument
Could not initialize graphics driver directfb:
Unsupported color depth.


But when i ran the links2 with -driver fb, it worked. I also tried to
run rage application which is supplied under EFL svn with the -dfb
parameter but it didn't worked either. Though again it worked with
-fb. Seems i have to do something more to use directfb. Maybe i am
basically doing something wrong. I am not sure thats why i am asking.
What is the fb and directfb difference? 

I asked the question at directfb list one of them suggested to install the lates stable directfb that is 1.2.6. Current one at the hardy repo is 1.0.1. &#304;f i want to install the 1.2.6 from source, how can i install it with the same location or 1.0.1 files. I dont want to use a double version of directb. I think configuring with prefix /usr should be fine but i want to be sure. Also i have some other libraries that are compiled by directfb enabled. Do i need to recompile them again after installing 1.2.6?


Thanx.

---

