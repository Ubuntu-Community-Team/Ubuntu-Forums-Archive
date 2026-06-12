---
title: "Dual screens, please post your xorg.."
date: 2009-06-27
forum: Desktop Environments
---

### Post by Jenkins1 on 2009-06-27
I am running 64bit jaunty on my laptop and have a Nvidia GeForce 8400M GS running the 180 driver. I am looking in to getting an external monitor that I can rotate to portrait and then back again. I am using a spare small display to experiment with. I have spent several hours goggling with limited success. 

I can get the external monitor to portrait with the xorg.conf attached. 
How ever when I use gedit to edit it i get this error "Xlib:  extension "RANDR" missing on display ":0.0"." Also my mouse gets stuck on the external display.

Also I can't use when removing the {option "rotate" "cw"}, restarting x and the trying xrandr -o left gets this error "Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing"

I would like to achive,

The ability to drag windows between displays maximizing in the current window only.

The rotation of the external monitor by the use of an icon on the desktop or similar.

If this doesn't make sense please ask.
Any thoughts, suggestions or advice would be appreciated.

---

### Post by Jenkins1 on 2009-06-27
attachment

---

### Post by SuperSonic4 on 2009-06-27
see attachment - although I run arch it should be much the same thing

---

### Post by Jenkins1 on 2009-06-27
> **SuperSonic4 said:**
> see attachment - although I run arch it should be much the same thing

Thanks for the quick reply. 
The use of twinview does solve the cursor getting stuck but in placing the      option "RandRRotaion"  "on"    line in rotates both screens. I would like only the external screen to rotate.

---

### Post by Jenkins1 on 2009-06-30
Bump!

Can I get one screen to rotate "on the fly" using randr -o command. Then I cans use xinearama and separate X windows.

---

