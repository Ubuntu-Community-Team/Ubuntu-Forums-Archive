---
title: "SCreen Display - GIMP (and others)"
date: 2006-07-08
forum: Desktop Environments
---

### Post by ColinG on 2006-07-08
Small problem folks and one that may have been raised before but I cannot find a reference - probably due to my poor searching ](*,) 

Anyway, taking GIMP as an example, if I open a blank canvas upon which to start drawing and then select a pen I can hold dowm the left mouse button and draw ok. If, however, I release the mouse button drawing should stop but it does not quite do that. If I drag the pen across the canvas without touching the mouse button it leaves a series of dotted line that reflect the pens journey across the canvas :(. If I minimise and then expand the GIMP window the dotted lines go away and things return to how they should be (only visible lines are the ones drawn by clicking on the pen).

There are other examples of this type of issue. It can happen when editing in Open Office where copies of the curser can be left between letters after highlighing.

My box is:
[LIST]
[*]Pentium D
[*]NVIDIA GeForce 6200
[*]1 gig RAM<
[/LIST]
Any ideas how I can stop this?

Many thanks
Colin

---

### Post by coolclassic on 2006-07-08
Do you have the nvidia drivers installed ?

---

### Post by ColinG on 2006-07-08
> **coolclassic said:**
> Do you have the nvidia drivers installed ?

Not sure I'm a real nube when it comes to things like Nvidia drivers. I did install the drivers that were packaged in Easyubuntu but apart from that I've no idea.

Guidance would be appreciated.How do I check and what do I do?

Many thanks
Colin

---

### Post by coolclassic on 2006-07-08
First have a look at /etc/X11/xorg.conf and look for the following entry:

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
    Driver         "nvidia"
#    BusID           "PCI:1:0:0"
   Option         "RenderAccel" "true"
#  Option          "AllowGLXWithComposite" "true" 
EndSection

You are checking the Driver selection if it reads nv then you don't have the nvidia drivers running.

---

### Post by ColinG on 2006-07-08
> **coolclassic said:**
> First have a look at /etc/X11/xorg.conf and look for the following entry:

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
    Driver         "nvidia"
#    BusID           "PCI:1:0:0"
   Option         "RenderAccel" "true"
#  Option          "AllowGLXWithComposite" "true" 
EndSection

You are checking the Driver selection if it reads nv then you don't have the nvidia drivers running.

Hi coolclassic, it reads nv :( . What should I do next.
Many thanks

---

### Post by ColinG on 2006-07-08
Cracked it. Thanks for the pointer coolclassic. That together with a Ubuntu howto has enabled me to get the correct driver in place.

Thanks\\:D/

---

