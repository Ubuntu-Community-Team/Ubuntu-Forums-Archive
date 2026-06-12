---
title: "evdev blues - unknown protocol still"
date: 2006-06-04
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-06-04
I'm trying to get my mx700 working in Dapper. Everything works but the side buttons. Found some info and edited my xorg.conf file. It now tries to use evdev but it fails saying

unknown protocol "evdev"

After searching the net found out that the evdev I had was broken. Got a link to a working one from the forums but still no luck. Exact same problem. I am using the package

xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb (apparently the working one)

Here is the section of code from xorg.conf

Section "InputDevice" 
   Identifier     "Configured Mouse" 
   Driver         "mouse"
   Option        "CorePointer" 
   Option        "Protocol" "evdev" 
   Option        "Dev Name" "Logitech USB Receiver" 
   Option        "Dev Phys" "usb-0000:00:02.0-3/input0"
   Option        "Device"   "mouse1 event3 ts1"
   Option        "Buttons" "10" 
   Option        "ZAxisMapping" "4 5" 
EndSection

If someone could help that would be great.

Thanks

Ironfistchamp

PS: Dapper ROCKS :-D

---

### Post by detyabozhye on 2006-06-05
Lookie here: [http://ubuntuforums.org/showthread.php?t=188302](http://ubuntuforums.org/showthread.php?t=188302)
the xorg.conf should look different in Dapper.

---

