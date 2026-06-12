---
title: "desktop effects cannot be enabled"
date: 2008-02-15
forum: Desktop Effects &amp; Customization
---

### Post by cobraking678 on 2008-02-15
Hi. I am an Ubuntu newb and desktop effects wont work.  I have a 256 mb Intel Corporation 82G965 Integrated Graphics Controller.  Please help!:)

---

### Post by snow_56767 on 2008-02-15
Hi,
   I suggest you look through synaptic (system > administration > synaptic package manager)
for your graphics card kernel source. It might be something like:
 integrated-kernel-source or something like that.
report back!

---

### Post by KLIA on 2008-02-15
same problem and when i run this command 

glxinfo | grep rendering

the output was yes and then later on it gives me this error

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
root@Linux:/home/waseem# 

my video card is nividia [RIVA TNT2 MODEL 64/MODEL 64 PRO] and 512 MB RAM

you think i can run the cube on using it

---

### Post by snow_56767 on 2008-02-15
Hi,
   KLIA, you should enter in the terminal:
```
sudo apt-get install nvidia-glx-legacy
```
This will install the driver needed for nvidia cards to be able to run compiz.
Then you need to install the kernel source.
Type:
```
sudo apt-get install nvidia-legacy-kernel-source
```
and don't forget to install  Xserver-Xgl
```
sudo apt-get install xserver-xgl
```
When you reboot your machine, a window might pop up saying
```
Ubuntu is currently running in low-graphics mode
if you wish to use 3D effects you must configure the card yourself
```
or something like that.
So configure you card with the correct driver: nv (nVidia Riva 128, RIVA, TNT GeForce)
and select your moniter from the drop down list on the first tab, It shouldn't be a Plug'n'Play.
Then see if compiz will work.

---

### Post by cobraking678 on 2008-02-16
I couldn't find any packages in Synaptic, but I found a driver for download at [http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html), but after I installed the 3D Mesa driver, desktop effects still dont work

---

### Post by cobraking678 on 2008-02-16
HI I ended up getting it to work by installing x-server xgl.  Thanks

---

### Post by riffmaster999 on 2008-02-22
Hi, i new to ubuntu i cannot enable my desktop effects, i have an ATI Radeon Xpress 200m Seres display driver.  
Any sugestions??

---

