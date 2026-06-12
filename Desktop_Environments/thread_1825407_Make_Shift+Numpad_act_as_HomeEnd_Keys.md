---
title: "Make Shift+Numpad act as Home/End Keys"
date: 2011-08-15
forum: Desktop Environments
---

### Post by raphaelr on 2011-08-15
In Ubuntu used to be a keyboard option called "Make Shift+NumPad work like MS Windows" or something. It allowed me to press for example Shift+NumPad 7 and it would get registered as the "Home" key. Without that option the shift key acts like a temporary NumLock and it'll pick up a "7" instead.
 
My regular Home/End keys are somewhat out of reach, so I wonder where the setting is in XFCE. I'm using the latest XUbuntu 11.04.

---

### Post by raphaelr on 2011-08-15
After some grepping I found the solution: You need to add the **numpad:microsoft** option to the **XkbOptions**. On older Ubuntus, do that in your xorg.conf. On newer ones open the file **/etc/default/keyboard** and change this line:
```
XKBOPTIONS=""
```
to
```
XKBOPTIONS="numpad:microsoft"
```
Save and reboot (restarting X doesn't seem to work, at least not with RAlt+PrintScreen+K).

---

### Post by nixahn on 2011-10-30
Thanks for this. This is a usual need for laptops, how would one go about suggesting the feature to be accessible from the settings configurator that comes with xfce? is it already there and I couldn't find it?

---

### Post by PT PinGuy on 2012-08-24
I install a derivation of Ubuntu 12.04 and I have the same issue. 

This solution works for me.

Thanks.

---

