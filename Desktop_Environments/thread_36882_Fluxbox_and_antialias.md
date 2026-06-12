---
title: "Fluxbox and antialias"
date: 2005-05-25
forum: Desktop Environments
---

### Post by *aLeX* on 2005-05-25
Hi all,

after some days of troubles I succeed in making fluxbox starting fast but now I've another problem. 
I can't select the antialias option in the config menu so I have only the ugly un-antialiased fonts  ](*,) 

Can anyone help me?

---

### Post by taavi on 2005-06-29
Hi!

I messing my head with compiling fluxbox 0.9.13 from source too.

Antialiasing is turned on with option -enable-xft,   which is default enabled. I passed it to ./configure ,but had no luck. Then I took a closer look at ./configure script output and saw this:

```
Package xft was not found in the pkg-config search path.
Perhaps you should add the directory containing `xft.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xft' found
Package xft was not found in the pkg-config search path.
Perhaps you should add the directory containing `xft.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xft' found
Could not link with Xft. Install Xft if you want support for it.
``` 

I checked libxft2 was installed. I installed libxft1 but had no luck. 

EDIT: I took a look into my gentoo install and found out that 'xft.pc' is part of xorg package ( x11-base/xorg-x11-6.8.2-r2 (/usr/lib/pkgconfig/xft.pc) ) . So I checked same directory in Ubuntu, but no xft.pc.

So how to get antialiasing and xft working in Ubuntu?

---

