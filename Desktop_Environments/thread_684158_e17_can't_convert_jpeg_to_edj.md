---
title: "e17 can't convert jpeg to edj"
date: 2008-01-31
forum: Desktop Environments
---

### Post by jazzykay on 2008-01-31
Hello, 

This is something that just recently started to happen. 
Basically, as of right now, I can't import any of my pictures into E17 to set as backgrounds. 
I get a message saying, background could not be imported due to conversion errors. 

I can import any edj background in easily. And the backgrounds that come with themes are working fine too.. It's just when i try to set a picture to a background that I get an error. 

$ sudo aptitude show enlightenment
Package: enlightenment
State: installed
Automatically installed: yes
Version: 1:0.16.999.042+cvs20080128-1gutsy2
Priority: optional
Section: x11
Maintainer: Debian Pkg-e Team <pkg-e-devel@lists.alioth.debian.org>
Uncompressed Size: 3461k
Depends: libc6 (>= 2.6-1), libcurl3 (>= 7.16.2-1), libdbus-1-3 (>= 1.1.1),
         libecore-con0, libecore-evas0, libecore-fb0, libecore-file0,
         libecore-imf-evas0, libecore-imf0, libecore-ipc0, libecore-job0,
         libecore-txt0, libecore-x0, libecore0, libedbus0, libedje0, libeet0,
         libefreet-mime0, libefreet0, libehal0, libembryo0, libevas0, libkrb53
         (>= 1.6.dfsg.1), libpam0g (>= 0.99.7.1), libssl0.9.8 (>= 0.9.8e-1),
         libx11-6, libxext6, enlightenment-data (=
         1:0.16.999.042+cvs20080128-1gutsy2), libevas-loader-eet,
         libevas-loader-jpeg, libevas-loader-png, libevas-saver-eet,
         libevas-saver-jpeg, libevas-saver-png, libevas-engine-buffer,
         libevas-engine-software-x11
Recommends: libevas-loaders-all
Suggests: emodules-all
Provides: x-window-manager
Description: The Enlightenment DR17 Window Manager
 Enlightenment is an advanced window manager for X11. Unique features include: a
 fully animated background, nice drop shadows around windows, backed by an
 extremely clean and optimized foundation of APIs. 
 
 This package contains the core files for Enlightenment DR17.

Anyone else having this issue? 

Thanks, 

jazz...

---

### Post by smartboyathome on 2008-02-01
Same here.

---

### Post by Heff on 2008-02-08
Do you have libedje-bin installed? That helped in my case.

---

