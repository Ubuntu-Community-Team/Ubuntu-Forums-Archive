---
title: "Mythtv compile problem"
date: 2006-04-16
forum: Desktop Environments
---

### Post by Smika on 2006-04-16
Hello,

I have a problem with installing Mythtv I use the howto from this forum. I want compile mythtv but i have this error. Is there someone that can help me?

root@Server:/opt/scr/mythtv-0.19# ./configure --prefix=/usr/local/mythtv-0.19
# Basic Settings
Compile type release
Compiler cache no
DistCC no
Install prefix /usr/local/mythtv-0.19
CPU x86 (model name : AMD Athlon(tm) XP 2000+)
Big Endian no
MMX enabled yes
Vector Builtins yes

# Input Support
Joystick menu yes
lirc support no
Video4Linux sup. yes
ivtv support yes
FireWire support no
DVB support no [/usr/include]
DBox2 support yes

# Sound Output Support
OSS support yes
ALSA support no
aRts support no
JACK support no
DTS passthrough no

# Video Output Support
x11 support yes
xrandr support yes
xv support yes
XvMC support no
XvMC VLD support no
XvMC pro support no
XvMC libs
OpenGL vsync no
DirectFB no

# Misc Features
DVD playback no
Frontend yes
Backend yes

Creating libs/libmyth/mythconfig.h and libs/libmyth/mythconfig.mak

./configure: line 2958: qmake: command not found
root@Server:/opt/scr/mythtv-0.19

Thanks, Smika

---

### Post by 146lily on 2006-04-16
I don't know much....but to compile a application you need all the development packages and GNU C++ compiler or similar. Plus all dependencies need meeting (can be tricky). At this point it become easy.

---

