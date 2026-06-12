---
title: "Glitchy KDE desktop graphics after installing ATI drivers"
date: 2007-03-01
forum: Desktop Environments
---

### Post by wosret on 2007-03-01
After trying (and failing) to set up the ATI proprietary drivers for my Radeon X1650, I discovered the 'Envy' script.  I ran that, and selected 'Uninstall ATI Driver' (to clean up the old versions) followed by 'Install ATI Driver'.  I chose all the default options.

After rebooting and logging in, all the windows and the KDE Panel were completely transparent.  Also, basically nothing would repaint itself unless i minimized and restored the window.  Here is a screenshot: [http://stuartp.commixus.com/uploads/stuart/snapshot1.jpg](http://stuartp.commixus.com/uploads/stuart/snapshot1.jpg)

After some fiddling with my xorg.conf, I found that these lines seem to control the problem:
```
#Section "Extensions"
#	Option	    "Composite" "Disable"
#EndSection
```

If these lines are commented out, the graphics on the desktop are fine, but fglrxinfo reports this:
```
stuart@stuartaw:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

When those lines are not commented out, the graphics are messed up, but fglrxinfo reports that it is using the correct renderer:
```
stuart@stuartaw:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6286 (8.33.6)
```
(also, the error about "XFree86-DRI missing" has disappeared)

I am using Kubuntu Edgy Eft (6.10) with its default versions of Xorg and KDE.  Here is a link to my xorg.conf: [http://stuartp.commixus.com/uploads/stuart/xorg.conf.txt](http://stuartp.commixus.com/uploads/stuart/xorg.conf.txt)

I don't know much about configuring X-Windows, so I really have no idea what I should try next.   Any help would be greatly appreciated!

 - Stuart

---

### Post by dave1507 on 2007-03-09
Hi, I have the same card and the same problem. It happens on Ubuntu, Kubuntu and openSUSE. Can anyone shed any light on this?

---

