---
title: "Kde compilation with konstruct"
date: 2005-08-23
forum: Desktop Environments
---

### Post by SeeLook on 2005-08-23
I try do it with Konstruct, i saw this topics:
[http://vtk.org/Bug/bug.php?op=show&bugid=1777&pos=0](http://vtk.org/Bug/bug.php?op=show&bugid=1777&pos=0)
and 
[http://ubuntuforums.org/showthread.php?t=11076&highlight=konstruct](http://ubuntuforums.org/showthread.php?t=11076&highlight=konstruct)
but it's not work. 
I add -lXxf86vm in gar.conf.mk file and install libxxf86vm-dev package, but it's not enought. I don't know where i have to put:
X11_Xext_LIB:FILEPATH=/usr/X11R6/lib/libXext.so;/usr/X11R6/lib/libXxf86vm.so
line (if this is correct).
I still have that errors:
/usr/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
when QT is compiling (i try skip it) and "info" in kcontrol,too.
Is somebody Who compiling KDE 3.4.2 under Kubuntu (Hoary) ??
(I made for it new user acount and does it without root rights)

---

### Post by tonysathre on 2005-08-23
try installing via apt-get or synaptic

---

### Post by SeeLook on 2005-08-23
:) 
Thanks for tip but.......
I've got kde 3.4.2 from repositories.
I want compile myself version with my cpu flags to make KDE faster, and try beta versions in future.

---

