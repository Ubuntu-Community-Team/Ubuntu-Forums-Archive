---
title: "Resolution  / 2-Port Issues"
date: 2005-12-13
forum: General Help
---

### Post by Canasta Thursday on 2005-12-13
I've searched all over the forums for an answer and have found nothing, but on the off chance that there is an answer, please excuse this thread.

Running both my Linux and Windows CPU by switching cords back and forth became a hassle (after only 3 days!), so I purchased a Belkin 2-Port KVm Switch.  I have just hooked up both computers, and to my dismay, the resolution on Ubuntu refuses to switch from anything but 640x480, no matter how many times I've tried to change it.  I went through Systems, Preferences, Screen Resolution, but it doesn't present any other options.  What do I do?

---

### Post by RAOF on 2005-12-13
I believe that this is caused by X being unable to get the acceptable resolutions from the monitor, so it defaults to something really safe.  Maybe you can turn off X's ask-the-monitor extension to fix this?

Somewhere in your /etc/X11/xorg.conf there will be a section like this:
```
Section "Module"
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

```
Try commenting out (adding a # to the start of the line) the "ddc" & "vbe" lines.  I think they are the modules responsible for monitor-autodetection.

---

