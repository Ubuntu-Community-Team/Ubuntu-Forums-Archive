---
title: "KDE's wacky dpi controlling"
date: 2005-10-06
forum: Desktop Environments
---

### Post by vh1 on 2005-10-06
hey there

has anyone noticed this?:
```
~$ startx -- -dpi 96
```
(my ~/.xinitrc script just opens xterm)
```
~$ xdpyinfo | grep resolution
```
and it will tell you something to the effect of "96x96 dpi"

launch kcontrol, change resolutions, then "xdpyinfo | grep resolution" again, and it will tell you something different

ie: I started with 96 dpi, changed from 1280x1024 to 1152x864 and my dpi was now 86x81

for now I have added "-dpi 96" to ServerArgsLocal in my /etc/kde3/kdm/kdmrc file and removed the unwanted resolutions from my /etc/X11/xorg.conf file, but now I pretty much live in fear of changing resolutions.

is there any way to stop kde from doing this?

---

### Post by HoPHP on 2005-10-19
Hi. I have a very similar problem:
When I start my computer normally, I have BIG fonts in KDE (even from KDM).```
~$ xdpyinfo | grep resolution resolution: 147x145 dots per inch 
```After restarting ONLY X, I have 100x100 (which is what I want (something like that) ).

Pretty bizarre!
What's your exact solution ?Adding -dpi 96 in kdmrc ? Bad bad bad solution, no? But works ?

Thanks, bye, HoPHP

P.S. Isn't there a bug report therefor ?

---

