---
title: "A Problem Compiling MPlayer:  X, ATI (FGLRX)?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by goodchild on 2005-11-08
Now, I'm trying to compile MPlayer (into a .deb, using fakeroot debian/rules binary) and encountering no problems during configuration, then on compiling this related series of "undefined reference" errors:

```
 /usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmUnmap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmUnmap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmClose'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmOpen'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmGetMagic'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmGetVersion'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmFreeVersion'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmMap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmMap'
collect2: ld returned 1 exit status
make[1]: *** [mplayer] Error 1
make[1]: Leaving directory
make: *** [build-stamp] Error 2
```

These all seem to have to do with X.  I installed the newest fglrx drivers from ATI  with no problems using a guide here.  

The driver package listing:

fglrx-control               8.18.8-1
fglrx-kernel-2.6.12     ""
fglrx-sources              ""
xorg-driver-fglrx         ""
**xorg-driver-fglrx-dev**  ""

Now, the last package seems relevant, it informs me that it:

"provides definitions for the GL and GLX extensions
and the FGLRXGAMMA extension interface library"

So it seems like this could be responsible.  Anyone have a guess at what my problem here is?  What do I do about it?

***

Solution:

Edit:  This was a problem with ATi's drivers.  They fixed it in the newest, and the Ubuntu repo version I believe doesn't suffer from this.

---

### Post by Ampersand on 2005-11-08
Looks like there might be a missing dependancy that wasn't picked up by configure... Do you have libgl1-mesa-dev installed?

---

### Post by goodchild on 2005-11-08
[QUOTE=Ampersand]Looks like there might be a missing dependancy that wasn't picked up by configure... Do you have libgl1-mesa-dev installed?[/QUOTE]

Yeah, I sure do.

---

### Post by taurus on 2005-11-08
Do you really want to compile it for your ubuntu or do you want to install it using apt-get???

---

### Post by goodchild on 2005-11-08
[QUOTE=taurus]Do you really want to compile it for your ubuntu or do you want to install it using apt-get???[/QUOTE]

I want to build an appropriate .deb package and install it.  Compiling it myself, on my machine has its own benefits and the deb will make it easier to uninstall if I find something better, upgrade, etc.

Lots of people do it.

Also, I used the gtk2 patch on the source.  Didn't mention it, as it doesn't seem to be causing it any trouble.

---

### Post by taurus on 2005-11-08
I am trying to present you with an easy solution to your problem but if you want to build it from source, then good luck.

---

### Post by bored2k on 2005-11-08
@taurus: building MPlayer from source is much better than getting an already compiled build. It's optimized for YOUR computer, it has pretty GTK2 support, it's the _latest_ -close to 1.0 final build (1.0pre)- and you can add a whole lot of codecs and options to it that normal distributable MPlayer builds wouldn't have.

@goodchild: I have never encountered that problem building my MPlayer packages, so I'm not sure if it's really a dependency problem, so here most of the files I usually install to get it compile (plus a whole bunch of compiled codecs):
```
sudo apt-get install build-essential libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0
```

Note: I prefer building MPlayer from CVS instead of using the stable package + gtk2 patch.

---

### Post by goodchild on 2005-11-08
[QUOTE=bored2k]
@goodchild: I have never encountered that problem building my MPlayer packages, so I'm not sure if it's really a dependency problem, so here most of the files I usually install to get it compile (plus a whole bunch of compiled codecs):
```
sudo apt-get install build-essential libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0
```

Note: I prefer building MPlayer from CVS instead of using the stable package + gtk2 patch.[/QUOTE]

I also very much doubt it is a dependency problem, as I have all the files you just listed already installed.  

***

So I found out a bit more about my problem.  The package libgl1-mesa-dev provides LibGL.a, which is in /usr/libs and glxext.o also exists within it.  Another provided by the same package is in /usr/lib/i686/mmx/cmov/.

---

### Post by bored2k on 2005-11-08
You could try #mplayer on freenode and poste them your problem using [nopaste]("http://www.rafb.net/paste/") ? They helped me quite a bit the first time I tried to compile.

---

