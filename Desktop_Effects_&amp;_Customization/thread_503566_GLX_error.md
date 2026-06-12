---
title: "GLX error ?"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by derby007 on 2007-07-18
I installed the latest Compiz and AWN .deb files, i changed my i810 driver to the 'intel' one (latest(2.0), ie. I have the intel 865G graphics. But when i run glxgears I get this error :: 
#glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

My xorg.0.log file says that glx is not loaded, direct rendering is > NO.

Can anyone point me in the right direction......??

Note: after I changed from i810 to intel, I can now get two more screen-resolutions, 1152x864 & 1280x768.
I'm running the latest Fiesty install.

---

### Post by derby007 on 2007-07-18
Bump::::
Did I forget to do some command after I installed the (.deb) Intel driver? 
Are theyre any other 'intel graphics' users out there that have got 3D running, ie. to get compiz-fusion & AWN ?

---

### Post by derby007 on 2007-07-19
i solved my glx proplem, i diverted the softlink for the libglx.so to the .../modules/extensions/liglx.so, but now i must try and get compizfusion working

---

