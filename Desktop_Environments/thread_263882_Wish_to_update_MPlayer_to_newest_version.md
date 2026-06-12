---
title: "Wish to update MPlayer to newest version"
date: 2006-09-23
forum: Desktop Environments
---

### Post by CaveRat on 2006-09-23
I would like to upgrade Mplayer to the latest version, but could use some help. I downloaded MPlayer-1.0pre8.tar.bz2 and extracted it to it's own folder. I'm still trying to figure out how to install programs I wish to check out. The lingo used for command line will take me a good while to sort and remember. I'm afraid someone will have to do a step by step for me, so I appologise for the inconvenience up front.
 Do I need to uninstall the old version first?

---

### Post by croak77 on 2006-09-23
You need to ./configure, make and sudo make install. I would uninstall mplayer .deb. first. Mplayer has  a few configure options depending on what kind of suppport you want. For example, --enable-gui --disable-arts --enable-x11  --enable-runtime-cpudetection --enable-sdl --enable-theora --with-win32libdir=/usr/lib/win32 --confdir=/etc/mplayer.

I don't know if there is a big difference between the mplayer package in the repo versus the one you downloaded. Might be easier to stick with the mplayer in multiverse.

---

### Post by got_nix on 2006-09-23
I agree with croak.. I really dont think there's much of a difference from the source build and the version in the repos's at all.

---

