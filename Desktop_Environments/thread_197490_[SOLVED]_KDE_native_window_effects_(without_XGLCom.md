---
title: "[SOLVED] KDE native window effects (without XGL/Compiz)"
date: 2006-06-15
forum: Desktop Environments
---

### Post by RavenOfOdin on 2006-06-15
Hey. I'm busy trying to figure out how to enable transparency and shadows on KDE windows - without Compiz - and I've pretty much gotten it working except for a few things which I need help with:

1) The Composite Manager crashes each time I log in to KDE, with the notice:

```

You must have Xorg > 6.8 for translucency and shadows to work. Additionally, you must have the following line in your xorg config file: 

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

I already have this in my xorg.conf file and these notices are still coming up. Why? 
I've included anything else I can think of to help composite and translucency along, such as : Option "backingstore" and : "AccelMethod" "EXA" 

. . .

2) Continuation of #1. . .Are xcompmgr and transset needed to correct this?

3) When the CM doesn't crash, KDE goes nuts and gives me a desktop interspersed with my splash screen.  The application menu looks like garbage and "Shut Down" button makes my screen darkening also look like garbage, sometimes with lines across it, sometimes not.

Is this a fault of the Xorg options "OpenGLOverlay" and "VideoOverlay"?

I'm using the fglrx driver (8.25.18 ) with the libGL.so.1 file from 8.18.6 located in my /usr/lib directory. I have an ATI Radeon 9200 SE (RV280.)

---

### Post by Treviño on 2006-06-26
Composite manager shouldn't work with ATi; i've not tested with dapper becouse now I've XGL, but with breezy wasn't possible... Just with nvidia.

---

### Post by Neo Ex on 2006-06-26
I have an ATI Radeon 9600XT and it doesn't work, too. I've tried this with Breezy, but it's ATI drivers' fault, because the Composite Manager has the development flag, so ATI doesn't support it and when you enable it, it will disable 3D acceleration.
So, you can't use fglrx if you want Composite Manager. You can try using the 'ati' driver, but you won't have 3D acceleration. If you have an ATI Radeon 9200 or below, you can use the 'ati' driver without problems (I think).

---

