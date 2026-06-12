---
title: "AIGLX Problems with Intel chipset I810... GLX missing on display"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by colinwalsh on 2007-10-01
I just installed feisty 7.04 on my HP tc4200 tablet with Intel chipset and i810 driver.  I'm trying to get compiz working, but my system doesn't seem to have any AIGLX capabilities.  I was under the impression that AIGLX worked on install.  When I run glxinfo the terminal outputs:

colin@colin:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Obviously there is something wrong there, I just don't know what it is.

If i try to execute the compiz file, the output is:

colin@colin:~$ compiz
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

I can post my xorg.conf file, which I've changed slightly based on the other posts i've seen on the forums, but nothing seems to have an effect on the glxinfo read out or the compiz functionality.  The xorg file does have the load "glx" and load "dbe" sections.  Any help would be greatly appreciated.  Thanks.

---

