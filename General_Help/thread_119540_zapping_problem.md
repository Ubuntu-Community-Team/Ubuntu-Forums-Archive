---
title: "zapping problem"
date: 2006-01-19
forum: General Help
---

### Post by superprotta on 2006-01-19
hi, i have a lifeview flytv platinum working fine with tvtime but tried to install zapping because it seemed to have a lot features wich tvtime doesn't have,as the teletext plugin or the recording function. the problem is that i get perfect audio but the screen remains black even if it seems to recognise correctly my card. if i try to change video to overlay mode i get this error message: ```
zapping_setup_fb failed
``` 
and this output from the terminal :
 ```
(C) 2000-2004 Iñaki G. Etxebarria, Michael H. Schimek.
This program is freely redistributable under the terms
of the GNU General Public License.

Using video device '/dev/video0', display ':0.0', screen 0.
Querying frame buffer parameters from X server.
DMA not possible on screen 0.
Setup failed. Try -vv for details.
```. 
so i tried to run zapping_setup_fb -vv and that's the output i get : 
```
(C) 2000-2004 Iñaki G. Etxebarria, Michael H. Schimek.
This program is freely redistributable under the terms
of the GNU General Public License.

Using video device '/dev/video0', display ':0.0', screen -1.
Querying frame buffer parameters from X server.
Xinerama extension not available
DGA extension support not compiled in
Screen 0:
  position               0, 0 - 1600, 1200
  frame buffer address   0x0
  frame buffer size      0x0 pixels, 0x0 bytes
  bytes per line         0 bytes
  pixfmt                 BGRA32_LE
DMA not possible on screen 0.
Setup failed.
```
anywonw knows how to solve it?

---

