---
title: "Rotate screen with openchrome on VIA CX700/VX700"
date: 2011-09-17
forum: Desktop Environments
---

### Post by MarianAl on 2011-09-17
Hello,

I have installed Xubuntu 11.04 on a small form-factor PC. The docs claim it is using a VIA CX700/VX700 chipset for graphics. 

I have connected a small 6.5" LCD with a native resolution of 640x480 (DM-65GS/TR). 

The install went smoothly. I have set things up to autologin to the graphical desktop and everything works fine. The desktop is a bit cramped on that resolution but that is not Ubuntus fault...

I inherited machine and screen as surplus and want to set it up with the tiny screen for a fun project that will require mounting the screen in portrait mode and I was hoping to rotate my desktop by 90 degrees. But I can't seem to manage that.

The UI for display settings on the desktop does not allow me to change the orientation, the button says "normal" and has no other options. So that is out.

I cannot change the orientation with xrandr:

```
#xrandr --output default --rotate left
xrandr: output default cannot use rotation "left" reflection "none"
```I have then created a file in /usr/share/X11/xorg.conf.d to specifiy a configuration and set the Rotate-Option:

```
Section "Device"
    ..
    Option "Rotate" "CW"
    ..
    Driver      "openchrome"
EndSection

```(The complete file is in the archive attached to this posting as is Xorg.log of this setup starting up)

This does rotate but now the startup of the system fails. Here's what happens:

Imagine my portrait-mode display, the display is taller than it is wide. On the top I can see the left part of a graphical login while there is a black area on the bottom. About a third of the screen seems to be outside of the right edge of my portrait-display. The login dialog that usually is centered appears offset to the right. Similarly the shutdown-button that normally is on the bottom right is not displayed.

The display is indeed rotated as I want it to be so that I can read the text and everthing appears upright. The mouse works as it should. 

So the overall effect is that of the image still being rendered 640wide x 480high and then rotated and displayed.

But what I need is a display that is 480wide x 640high.

In addition to that the autologin fails and I cannot login manually as well. It always returns me to the broken login screen.

Thanks for reading this far, I hope I am making sense. I can provide more details on request and am looking forward to try anything you may suggest.

Ciao, MM

---

