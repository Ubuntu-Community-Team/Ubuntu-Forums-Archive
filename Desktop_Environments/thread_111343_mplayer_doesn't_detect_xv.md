---
title: "mplayer doesn't detect xv"
date: 2006-01-02
forum: Desktop Environments
---

### Post by Paby on 2006-01-02
Hi all,

I'm trying to compile mplayer but during ./configure it doesn't detect xv or the other major video output methods so I can't play any videos:

Checking for X11 headers presence ... not found (check if the dev(el) packages are installed)
Checking for X11 libs presence ... not found (check if the dev(el) packages are installed)
Checking for X11 ... no
Checking for DPMS ... no
Checking for Xv ... no
Checking for XvMC ... no


I guess I'm missing some packages but can't figure out which ones. Any clues?

Thanks!

---

### Post by hw-tph on 2006-01-02
A good start would be installing the xlibs-dev meta-package. It will cover all the essential X development libraries.


H&#229;kan

---

### Post by kaamos on 2006-01-02
Have you seen this? [http://ubuntuforums.org/showthread.php?t=85190](http://ubuntuforums.org/showthread.php?t=85190)

[quote=bored2k]```
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0 fakeroot
```[/quote]

---

