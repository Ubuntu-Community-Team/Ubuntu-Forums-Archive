---
title: "mplayer (-vo) device"
date: 2006-07-03
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-07-03
I thought I had this all taken care of but I think after the last kernel update I must have changed something because now every time I try to run anything in mplayer I get 

***Error opening initializing the selected video_out (-vo) device***

I have checked the /etc/mplayer/mplayer.conf file and its still set the same as always. I also redownloaded the Win32 essentials (codecs) from mplayers site and I still get this error.

Any ideas?

---

### Post by Thund3rstruck on 2006-07-03
Ok, so I figured out what caused the failure. I upgraded to the 686  kernel and so I needed the 686 package. Now how do I configure mplayer.conf file? What do I set as the vo device?

---

### Post by Thund3rstruck on 2006-07-03
nevermind.. mplayer vo=sdl worked for me.

Available video output drivers:
        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        tdfxfb  3Dfx Banshee/Voodoo3/Voodoo5
        3dfx    3dfx (/dev/3dfx)
        xvmc    XVideo Motion Compensation
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        ggi     General Graphics Interface (GGI) output
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        aa      AAlib
        caca    libcaca
        dxr3    DXR3/H+ video out
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

91 audio & 204 video codecs

---

