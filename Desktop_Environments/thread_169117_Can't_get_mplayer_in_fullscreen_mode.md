---
title: "Can't get mplayer in fullscreen mode"
date: 2006-05-01
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-05-01
i have been having mplayer,it is great but i can't get fullscreen to work.in fullscreen mode the size remains the same,anybody know how to rectify this??

---

### Post by Stewart on 2006-05-01
In mplayer goto preferences-->video and try one of the other drivers.

Its worth a try.

Stewart

---

### Post by jazzmuzik on 2006-05-02
As Stewart was saying, try a different driver. If you are running mplayer on the command line you can get a list of available video output drivers with this:

```
mplayer -vo help
```

I my system I get:

```
Available video output drivers:
        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        3dfx    3dfx (/dev/3dfx)
        tdfxfb  3Dfx Banshee/Voodoo3/Voodoo5
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
        svga    SVGAlib
        aa      AAlib
        caca    libcaca
        vesa    VESA VBE 2.0 video output
        directfb        Direct Framebuffer Device
        dfbmga  DirectFB / Matrox G200/G400/G450/G550
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

```


Then you can test each one:

```
mplayer -vo xv movie.avi
mplayer -vo gl2 movie.avi
mplayer -vo gl movie.avi
mplayer -vo sdl movie.avi

```etc.

The caca option is pretty wild. It will convert a movie into colored ascii text chacters. Looks okay from a distance. Yup, if renders a movie in ascii characters.

---

### Post by akshaysrinivasan on 2006-05-02
it worked with xv,thanks a lot.

---

### Post by dimatrod on 2006-05-10
How can I get the Xv video driver working under the GUI?  Do I need to re-compile?  If so, what do I have to put after ./configure --enable-gui

---

