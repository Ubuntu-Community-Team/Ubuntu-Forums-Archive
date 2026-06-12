---
title: "xawtv problem"
date: 2006-01-05
forum: Desktop Environments
---

### Post by menollo on 2006-01-05
when i run xawtv i get an error:
Error: Aborting: no fontset found

I'm running Ubuntu 5.10...

can someone help me?

thx, Jacco

edit: this is the output:

root@menollo:/$ xawtv

This is xawtv-3.94, running on Linux/i686 (2.6.12-10-k7)
WARNING: Your X-Server has no DGA support.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,  -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*,*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

---

### Post by kimera on 2006-01-13
I have problem with xawtv too.
Does xawtv support v4l2? Because I have a webcam that work fine with gnomemeeting but with xawtv!!

some output

kimera@kiddo:~$ xawtv -hwscan
This is xawtv-3.94, running on Linux/i686 (2.6.12)
looking for available devices
port 61-61
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : SN9C10x PC Camera
    flags:  capture

kimera@kiddo:~$ sudo xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.12)
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xbfad3184 [PAL_G,PAL_K,PAL_M,NTSC_M,NTSC_M_JP,SECAM_B,SECAM_G,SECAM_H,SECAM_K1,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null)]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
game over
kimera@kiddo:~$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=0xf0000000
/dev/video0 [v4l2]: no overlay support
kimera@kiddo:~$

I will apreciate every suggestion!
Thanks a lot

---

