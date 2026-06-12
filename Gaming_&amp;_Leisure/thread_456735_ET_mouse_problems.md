---
title: "ET mouse problems"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by jmccnz on 2007-05-28
Hi there,

I am having a problem in ET.

When I have a keyboard button pressed down, the mouse inside et will not work at all. That means I cannot run and turn at the same time, making it practically impossible to play.

This is not an issue outside of ET on the desktop however.

Has anyone ever come across this before? Anybody have an idea how I can fix it?

---

### Post by jmccnz on 2007-05-28
Just rechecked and it actually does occur on the desktop also.

---

### Post by asipi on 2007-05-29
what kind of keyboard and mouse you have?

---

### Post by jmccnz on 2007-05-29
Apple bluetooth keyboard and Mighty Mouse. Cheers

---

### Post by jmccnz on 2007-05-30
Anyone at all know? It doesn't happen in Mac OS X so it must be a problem with my Apple gear and linux... Anyone?

---

### Post by asipi on 2007-05-31
I guess it's USB-bluetouth keyboard and mouse, could be that the handling of such devices in the kernel is not proper... try ordinary keyboard and mouse, I recommend PS/2 connection type (and remove the bluetouth devices before use tha previous ones).

If the problem will still exist, then it won't related to your bluetouth devices but your system settings... (somehow we have to be sure about this, then we can find out the next step)

---

### Post by jmccnz on 2007-06-01
Only problem is, I don't have any PS/2 gear handy and my computer (intel iMac) has no PS/2 ports, meaning I would need to go through USB with an adapter

---

### Post by asipi on 2007-06-01
yep... too bad... ;)
so try a non bluetouth keyboard+mouse to ensure if your problem does not come from the bluetouth

---

### Post by jmccnz on 2007-06-01
I am typing this with a regular USB keyboard and mouse. The problem is still there.

Thanks

---

### Post by asipi on 2007-06-01
Tip:
the mouse and the keyboard are on the same usb-hub/controller or your usb port is not 2.0 compatible :(
practically I do not have an idea how to solve this due to lack of deeper knowledge, but I recommend to open a thread in the Hardware forum, because it is more hardware related than gaming, and I guess the hardware guys are not reading the gaming forum ;)

If it works in osx than could be you need to change the default usb drivers only, or set any parameter for the kernel, so I think you have a good chance to get it work.

---

### Post by jmccnz on 2007-06-01
Thanks for your help.

I found the solution, something about deleting mouseemu...

Thanks anyway!

---

### Post by asipi on 2007-06-01
omg, the emulating of the 3rd button was switched on? :P
It is useful only for 2 buttons mouse... but who has one nowadays :D
Never thought about it, thanks for the info and gratulations :D

---

