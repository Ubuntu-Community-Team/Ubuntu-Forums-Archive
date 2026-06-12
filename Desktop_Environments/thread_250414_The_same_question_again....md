---
title: "The same question again..."
date: 2006-09-04
forum: Desktop Environments
---

### Post by tribunal on 2006-09-04
Hi all
I have Kubuntu 6.06, Nividia videocard (GeForce 6600...)
So, I decided to try Xgl and compiz
I have installed nvidia drivers and checked them. It works
Now I have installed Xgl.
And tried to replace X with Xgl.
So, it works strange. (!!) And I think this is my main problem :(
I have spent 5 hours ](*,) , but it still  works very very slow and buggy :(
my polyester theme looks bad..
Konsole started to work bad and buggy :(
There is strange points between symbols
Well, Xlg is in memory, so I decided to try compiz
And.. and it doesn't start at all :(

P.S. I have used two guides: from here and from compiz.net

P.P.S I have installed the latest versions of Xgl, compiz, cgwd

---

### Post by someguyouknow on 2006-09-04
Not sure what is wrong but posting your /etc/X11/xorg.conf contents could hold the answer.

---

### Post by tribunal on 2006-09-04
this is my xorg.conf: (not all, just device part)
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    Option      "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    BusID          "PCI:1:0:0"
EndSection

In modules Load "glx" is enabled

#Section "Extensions"
#  Option       "Composite" "off" (I don't know is it right?)
#EndSection

This is my kdmrc:

ServerCmd=/usr/bin/Xgl -br -ac -accel glx:pbuffer -accel xv:pbuffer

I have commented last line in /usr/bin/displayconfigrestore (#main())

For now it is all

And without Xgl (with just X) glxgears works fine and smoothly

---

