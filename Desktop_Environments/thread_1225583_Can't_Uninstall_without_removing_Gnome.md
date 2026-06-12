---
title: "Can't Uninstall without removing Gnome"
date: 2009-07-28
forum: Desktop Environments
---

### Post by bnshrdr on 2009-07-28
I want to uninstall all totem packages on my system, but when I try, it tells me it needs to then remove gnome-desktop-environment, along with many other gnome components.  Here is what I am executing:
```
sudo apt-get --purge remove totem\*
```
Anyone know what the problem is?

By the way, I am using Jaunty and have installed from the mini iso and have downloaded and installed gnome myself.

Any help will be greatly appreciated!

---

### Post by philcamlin on 2009-07-28
why dont you try

sudo apt-get remove totem

any different?

---

### Post by bnshrdr on 2009-07-28
Sorry.  I have tried that, it tells me that the package totem has already been removed or something along those lines, but clearly it hasn't.  So far on this system, the only thing I have installed that wasn't through the package manager was ffmpeg, which I compiled from source.

---

### Post by vinutux on 2009-07-28
> **bnshrdr said:**
> Sorry.  I have tried that, it tells me that the package totem has already been removed or something along those lines, but clearly it hasn't.  So far on this system, the only thing I have installed that wasn't through the package manager was ffmpeg, which I [COLOR="Red"]compiled from source[/COLOR].

perhaps that is prob....related to uninstall totem...

Y are u try to compile ffmpeg from source....all that pakages in  official repo................

---

### Post by bnshrdr on 2009-07-28
I needed support for libx264, so I had to recompile it with the flag --enable-libx264.  This really shouldn't affect totem, should it?

---

### Post by vinutux on 2009-07-28
I think so.....both x264 and libx264 are in repo

totem use gatreamer framework....not direct related to gnome...i think buil currupted your software-source database......

---

