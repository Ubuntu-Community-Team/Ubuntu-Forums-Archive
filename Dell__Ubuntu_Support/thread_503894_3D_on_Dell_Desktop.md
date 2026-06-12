---
title: "3D on Dell Desktop ?"
date: 2007-07-18
forum: Dell  Ubuntu Support
---

### Post by derby007 on 2007-07-18
I have a Dell desktop with Fiesty, Intel 865G graphics, using intel driver (changed from i810), but I am now getting a GLX error. 
I installed the latest Compiz and AWN .deb files, i changed my i810 driver to the 'intel' one (latest(2.0), ie. I have the intel 865G graphics. But when i run glxgears I get this error :: 
#glxgears
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

My xorg.0.log file says that glx is not loaded, direct rendering is > NO.
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Can anyone point me in the right direction......?? Have u got similar specs??

Note: after I changed from i810 to intel, I can now get two more screen-resolutions, 1152x864 & 1280x768.

---

