---
title: "alter xorg.conf to prevent gnome loading but to load the graphics card drivers"
date: 2012-09-21
forum: Desktop Environments
---

### Post by mzycdth on 2012-09-21
Hi guys,

Two things, one problem(?xorg.conf?) with my home server:

1. I would like my ubuntu 12.04 server (64 bit) to load into terminal not into GDM (gnome 3 installed for server side maintenance)

2. Currently when I boot the server headless I have problems with a GPU tool (cgminer) which claims that graphics devices have been disabled, I believe this is due to a confusion with onboard GFX and my ATI 5850 card if there is no resistance on any of the ports during loading.

Could somebody talk me through any necessary config changes to fix these two issues?

I have changed the file to be very basic:

```

Section "Module"
    Load "GLX"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth 24
Endsection

```

Many thanks

---

