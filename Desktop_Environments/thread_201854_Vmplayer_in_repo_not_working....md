---
title: "Vmplayer in repo not working..."
date: 2006-06-22
forum: Desktop Environments
---

### Post by apoclypse on 2006-06-22
I keep getting this error everytime  i try to run vmplayer. I 've tried it on 2 different machines and both have the same error. 

```
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:6481): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)

(vmplayer:6481): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-19317/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

```

---

### Post by dannystaple on 2006-09-04
Have you seen this thread: [vmplayer not loading - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=190321")

Unfortunately, trying that just leads vmplayer to silent fail on my box. I will have to go back to the non repo version which worked just fine.

Danny

---

