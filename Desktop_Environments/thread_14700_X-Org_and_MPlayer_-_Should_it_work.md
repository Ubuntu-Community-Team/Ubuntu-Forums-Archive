---
title: "X-Org and MPlayer - Should it work?"
date: 2005-02-09
forum: Desktop Environments
---

### Post by WillCooke on 2005-02-09
(Cross Posted from Hoary Dev)

Hi All,

OK, I've installed Hoary and I'm trying to compile MPlayer.  I resolved a lot of the problems, but now I'm stuck.

In order for MPlayer to display anything on the screen, and also to make use of the GUI it would seem that it needs X11  from XFree86.  Should it work with X-Org?

The problem is this from configure.log of MPlayer...


============ Checking for X11 headers presence ============
Result is: yes (using /usr/X11R6/include)
##########################################

============ Checking for X11 libs presence ============
Result is: yes (using /usr/X11R6/lib)
##########################################

============ Checking for X11 ============

#include <X11/Xlib.h>
#include <X11/Xutil.h>
int main(void) { (void) XCreateWindow(0,0,0,0,0,0,0,0,0,0,0,0); return 0; }

cc     /tmp/mplayer-conf-13217-7589.c -o /tmp/mplayer-conf-5336-7589.o -I/usr/X$/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 65539 >= 116$/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 65539 >= 116$/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 16777216 >= $/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 65539 >= 116$/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 16777216 >= $/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 65539 >= 116$/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 65539 >= 116$/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 16777216 >= $/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 65539 >= 116$/usr/bin/ld: /usr/X11R6/lib/libX11.a(Xrm.o): invalid string offset 16777216 >= $/usr/X11R6/lib/libX11.a: could not read symbols: File format not recognized
collect2: ld returned 1 exit status

ldd /tmp/mplayer-conf-5336-7589.o
ldd: /tmp/mplayer-conf-5336-7589.o: No such file or directory

Result is: no
##########################################


So, as far as I can tell, all the libs are there, but not the ones needed.  Am I right?  :confused: 

MPlayer compiles OK without the --enable-gui option and I can play, for example an XVid movie.  I can hear it, but I can't see it.

If I do an MPlayer -vo help I get


Available video output drivers:
        vesa    VESA VBE 2.0 video output
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

So, no X11 type output available.  (That'll be why I cant see anything then!)

Anyone got any ideas?  

As an aside, has anyone noticed Firefox seg-faulting more than usual?

Thanks for any pointers you can give,

Will

---

### Post by rosslaird on 2005-02-09
I can't give you any insight about how to fix your problem, but I am fairly sure that mplayer works with xorg -- well, I'm certain of it, since I was using mplayer and xorg with both Debian Sid and Gentoo (I haven't yet put it on my Ubuntu install, however). So I don't think xorg is the problem.

You might try looking in the Xorg.0.log file (in /var/log) and in xorg.conf, and in .xsession-errors for some snippet of insight.

---

### Post by valadil on 2005-02-09
It works fine for me.  Though I got it through apt instead of compiling myself.

---

### Post by gheorghe_pop on 2005-02-09
i'm using hoary with compiled mplayer and xorg no problem here.

---

### Post by WillCooke on 2005-02-09
Thanks all.

I wanted to build from source to make sure I turned on all the extra bits and bobs just the way I like them.

I have solved the problem!

[COLOR=SlateGray]apt-get clean[/COLOR]

To clear out the .deb packages from the cache

[COLOR=SlateGray]apt-get install --reinstall libx11-6 libx11-6-dbg libx11-dev[/COLOR]

To re-download and install **all** the X11 libs.

And hey presto.

(Well, I say that, ./configure now says X11... Yes, rather than 'no' so I'm getting there)

---

