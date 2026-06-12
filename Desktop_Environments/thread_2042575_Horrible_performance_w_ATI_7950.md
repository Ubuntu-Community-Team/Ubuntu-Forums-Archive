---
title: "Horrible performance w/ ATI 7950"
date: 2012-08-14
forum: Desktop Environments
---

### Post by donbowman on 2012-08-14
I'm not sure what i'm doing wrong.
I have a desktop running Kubuntu 12.04 64-bit. Core-i5 @ 2.7GHz.
It had an Nvidia GT240 in it, and this worked really well: very fast graphics, vdpau dispatched all video fluidly, etc.

I then upgraded one monitor and the video card.
Its now a 2-head 2560x1440 [display-port] and 1200x1920 [dual-link dvi]. The 1200x1920 is obviously rotated 90 degrees. This is done using randr (kde 'display settings'). With the Nvidia it was done using their TwinView (so i could keep VDPAU).

Combined this gives a 3760x1920 single screen.

The video card is an ATI/AMD RADEON HD 7950. It is running @ 1GHz core, 1250MHz DDR5 RAM. I've checked w/ aticonfig, it loafs @ 500MHz when idle, and kicks to 1GHz when i move windows etc.

I have **terrible** performance. Its obvious just moving windows around the screen. Mplayer (using Xv or gl. vaapi doesn't work well) is not able to keep up with even 720p videos (which should all work fine in just sw on my cpu). Youtube can't keep up. And, i know its not a benchmark, but 'glxgears' gives ~600fps. And fgl_glxgears gives ~215fps. Yes glxinfo shows direct rendering enabled.

in fullscreen, glxgears is 24fps, and very jerky.

I'm kind of @ my wits end. This card should be head and shoulders faster than the GT240 i replaced. But its a slug. I must have something configured wrong.

I am running the fglrx driver 2:8.960-0ubuntu1.1. I did try the xorg-edgers, but there were compile problems around TS_USEDFPU. Yes i know it was supposed to be fixed there, but nonetheless...

fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series 
OpenGL version string: 4.2.11627 Compatibility Profile Context


This is my [xorg.conf]("http://pastebin.com/scqtkFCs"). 
Other files that are likely of relevance:
 * [xrandr]("http://pastebin.com/GrJUpcqG")
 * [Xorg.0.log]("http://pastebin.com/hfDTraL6")
 * [dpkg -l]("http://pastebin.com/0Rc6QjjN")
 * [glxinfo]("http://pastebin.com/0cMPBpfh")
 * [xdpyinfo]("http://pastebin.com/C0pMGYEp")

$ vainfo 
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD


$ uname -a
Linux server 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

(i've tried upgrading / downgrading kernel to get the TS_... build issue solved on the xorg-edgers ppa of fglrx but to no avail, and no perf difference anyway).

So, um, help? What would you check or do?

---

### Post by draki on 2012-08-22
Hi donbowman,

I have almost the identical problem - I have a AMD Radeon HD 7700 Series card

 glxgears gives me ~560 fps windowed, fgl_glxgears ~130 fps, but fullscreen glxgears gives me 13 fps!!!

I switched from using displayport to hdmi and that seems to reduce the number of random crashes (so far anyway)

I've also reverted to the Ubuntu suggested drivers rather than 12.8 from the AMD website as they seem to be slightly more stable...

But I'm at a loss as well...

I used to have an nVidia 9800gt - this should be significantly more powerful, but is awful in comparison :( Not happy at all

Help!

---

### Post by QIII on 2012-08-22
vaapi is not supported in mplayer, but there is a ppa version that has it added -- it's mplayer-vaapi.  I'll try to remember to get back to this tonight when I get home.

Did you both uninstall the NVIDIA driver before installing the ATI driver?  Have you used CCC to optimize your performance?

I get silky smooth 1080p playback on mplayer-vaapi.  I'll let you know how I have CCC set up.

---

### Post by draki on 2012-08-23
Thanks QIII - that would be most helpful

I tinkered once again yesterday evening and purged all drivers (nVidia went as soon as I installed Ubuntu, so yes) - installing AMD Catalyst 12.8 Proprietary Linux x86 Display Driver

and finally managed get Diablo 3 running under Wine and Ubuntu 2d at a good framerate

Only had one crash so far...

but - and this is irritating and hardly the most critical of problems - my screensaver (Helios from RSS) runs terribly slow.. When launched in a window from the command line it's a thing of beauty

I'd be very interested in your CCC config

thanks very much for your help

---

### Post by draki on 2012-08-24
I manged to massively improve my performance by tweaking Compiz...


in CCSM under OpengGL I enabled sync to vblank
under Composite I disabled 'detect refresh rate' and enabled 'unredirect fullscreen windows'
I also set the refresh rate to 75, even though my screens are 60

glxgears are now 700-800 fps windowed and 40 or so fullscreen (not ideal yet)
and fgl_fxgears is 800+ fps even hitting over 1000 for a while

---

### Post by donbowman on 2012-08-25
> **QIII said:**
> vaapi is not supported in mplayer, but there is a ppa version that has it added -- it's mplayer-vaapi.  I'll try to remember to get back to this tonight when I get home.

Did you both uninstall the NVIDIA driver before installing the ATI driver?  Have you used CCC to optimize your performance?

I get silky smooth 1080p playback on mplayer-vaapi.  I'll let you know how I have CCC set up.

i indeed have the vaapi ppa for mplayer. i find it unreliable. its fast, but lots of corruption.

i did not uninstall the nvidia intially, but have subsequently (and have reinstalled the fglrx since).

the performance is obvious just moving windows around. its not awful, but not in the league for this card. and the opengl 'benchmarks' glxgears/fgl_gears are way off.

if i swap the kde settings to use opengl for effects, the entire thing slows to a crawl... windows are hard to move, etc. i think this is a clue. but i don't know where else to look other than all the files i included above.

i'm near my wits end and about to go back to the gt240. it was pretty fast.

---

### Post by donbowman on 2012-08-26
is anyone else running with RandR to rotate one display?

If i set compositing to 'OpenGL' in KDE Desktop Effects, and enable desktop effects (alt-shift-F12), the system slows to a crawl. fgl_glxgears gets ~7fps. windows hardly can be moved, takes ~10s to open a new window, etc.

If i disable desktop effects, its better, i'm back to the original 'merely very slow for such a good card' problem.

---

### Post by donbowman on 2012-08-26
for mplayer,
$ mplayer -cache 16384 -ao null -vo vaapi <file>

Starting playback...
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=1.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vaapi] 1280x720 => 1280x720 H.264 VA-API Acceleration  [fs]
[VD_FFMPEG] XVMC-accelerated MPEG-2.
A:   3.4 V:   3.0 A-V:  0.454 ct:  0.104   0/  0 10% 108%  0.2% 63 0 87% 


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

and its obviously dropping a frame once in a while. not every frame, just some.


$ vainfo 
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

---

