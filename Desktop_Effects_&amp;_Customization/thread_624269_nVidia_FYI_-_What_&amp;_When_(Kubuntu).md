---
title: "nVidia: FYI - What &amp; When (Kubuntu)"
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by mpierce on 2007-11-26
There is a lot of confusion about how to set up the xorg.conf file. Hopefully, this will help a lot of people when setting up Compiz

1) There are two xserver that will work a) AIGLX - this is now in-built into xserver and b) XGL - this is a separate package that has to be installed. XGL is a little more bleeding edge and less stable but is the one I use.

If you use AIGLX, you will need the following modules in your /etc/X11/xorg.conf
  Section "Module"
   Load "dri"
   Load "dbe"
   Load "glx"
  Section "Device"
   Option "XANNoOffscreenPixmaps"
   Server "Screen"
   Option "AIGLX" "true"

uncomment
   Section "DRI"
   Mode 0666
   EndSection

insert
   Section "Extensions"
   Option "Composite" "true"
   EndSection

Save the file and glx is now working on your nVidia card if you are using nvidia-glx (don't know about nvidia-glx-legacy as the card often did not support glx).

If you are using XGL
   Server "Screen"
   Option "AddARGBGLXVisuals" "true"

insert
   Section "Extensions"
   Option "Composite" "true"
   EndSection

I'm using a nVidia 6200 with 256Mb of ram. nVidia says that the section on extensions and AddARGBGLXVisuals is probably not needed (see - [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-b.html) )
This explains what all the options do for a nVidia card

From terminal to check if you are using glx:
   glxinfo | grep direct <enter>
direct rendering: Yes

Compiz works perfectly on my old AMD Athlon 1.33 with a new nVidia 6200 card. I've not had to insert things like:
   ServerCmd=/usr/bin/Xgl -fullscreen -ac -accel xv:fbo -accel glx:pbuffer
This is all working with the new driver and XGL is turned on and used by your xorg.conf file. 

The cpu useage is very low until I enable Cube gears then usage is off the planet! (70-80%)

Hope this helps...

---

