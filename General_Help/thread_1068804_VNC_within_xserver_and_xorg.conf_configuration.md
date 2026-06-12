---
title: "VNC within xserver and xorg.conf configuration"
date: 2009-02-13
forum: General Help
---

### Post by PierreM on 2009-02-13
Hi!

I am trying to get VNC to work within my xserver. For that I use something called xf4vnc ([http://xf4vnc.sourceforge.net/modular.html](http://xf4vnc.sourceforge.net/modular.html)). I followed all the steps and got everything to compile, however I am having a problem with the xorg.conf set up:

I am supposed to add the following :

[Section "ServerLayout"
....
 InputDevice "vncMouse"    "ExtraPointer"
 InputDevice "vncKeyboard" "ExtraKeyboard"
....
EndSection

# Don't replace this section, add the Load "vnc" line to your existing Section.
Section "Module"
...
 Load "vnc"
....
EndSection

Section "InputDevice"
 # vncKeyboard: keyboard actions from vnc
 Identifier "vncKeyboard"
 Driver "rfbkeyb"
EndSection

Section "InputDevice"
 # vncMouse: mouse actions from vnc
 Identifier "vncMouse"
 Driver "rfbmouse"
EndSection


When I restart X, I am directly going into low mode graphic. If I remove the 2 lines
 InputDevice "vncMouse"    "ExtraPointer"
 InputDevice "vncKeyboard" "ExtraKeyboard"

X starts fine, xdpyinfo shows me that the vnc module is loaded. However, when I run a vncviewer I get the desktop but my mouse and keyboard simply do not work. I assume that the 2 lines I removed must be important.

I use Ubuntu Hardy and i have a nvidia Quadro FX 350M graphic card. With the 2 lines, my Xorg.0.log shows that VESA is used and i get:
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Would any one know why these 2 lines do not work, as I understand that they are absolutely required in order for the (or any) VNC server to recognize mouse/keybd events?

Thanks!

    -Pierre

---

