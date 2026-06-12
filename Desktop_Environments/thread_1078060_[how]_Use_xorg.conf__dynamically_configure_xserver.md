---
title: "[how] Use xorg.conf  dynamically configure xserver"
date: 2009-02-22
forum: Desktop Environments
---

### Post by stranger88 on 2009-02-22
Hi all,

I need to configure MinX,MinY,MaxX and MaxY dynamically(my xorg.conf).
How can I do it?

Is there some kind of an X interface that can configure a touch screen at run-time making it possible to dynamically configure the hardware at session startup without having to restart.

**my xorg.conf:**
Section "InputDevice" 
   Identifier "touchscreen0" 
   Driver "evtouch" 
   Option "Device" "/dev/input/event5" 
   Option "DeviceName" "touchscreen" 
[B]   Option  "MinX" "212"
   Option  "MinY" "262"
   Option  "MaxX" "4123"
   Option  "MaxY" "3865"[/B]
   Option "ReportingMode" "Raw" 
   Option "SendCoreEvents" 
EndSection

thanks

---

