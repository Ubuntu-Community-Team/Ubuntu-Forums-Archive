---
title: "PS3 Controller no longer working"
date: 2013-06-27
forum: Gaming &amp; Leisure
---

### Post by EricGraham1987 on 2013-06-27
So originally I had my PS3 controller hooked up via USB. I was using it for my emulators a bit then it stopped working after I installed xboxdrvr and qtsixa. I wanted to find a program like motioninjoy for linux. Does anyone know how I can get my PS3 controller working again? I am not a computer noob but I am a linux noob.

---

### Post by J.K.Makowka on 2013-06-29
I couldn't get qtsixa to run either, but with the xboxdrvr is it working fine for me. The trick is that you have to run it in a terminal in the background to have it working.

Edit: start it via: "sudo xboxdrv --detach-kernel-driver"

I have a 3rd party USB PS3 controller. Why it works only with admin rights is unclear to me also.

Edit2: This has some further details:
[http://danielj.se/2013/04/26/how-to-get-your-playstation-3-dualshock-3-sixaxis-controller-to-work-on-linux/](http://danielj.se/2013/04/26/how-to-get-your-playstation-3-dualshock-3-sixaxis-controller-to-work-on-linux/)

And this should have some details how to have it run permanently in the background as a deamon:
[http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html](http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html)

---

### Post by Ranko Kohime on 2013-07-01
It requires root privileges because even administrative users (such as the first account created on a new install) don't belong to the group that is allowed to control input hardware (i.e., gamepads/joysticks)  There are workarounds to that, however, but they do get somewhat involved.

I haven't had much luck with qtsixa, as it relies on sixad, and it fails to launch sixad correctly.  However, using sixad alone does yield a usable controller for me.  (In as far as usable goes, there is nowhere near as much support in Linux games for controllers as there is in Windows games, in my experience)

---

### Post by colemanmg on 2013-07-01
My son controller stopped working about a week ago for no reason..is there a issue with these PS3 Controlers

---

