---
title: "USB drive automount doesn't work from all usb ports"
date: 2006-06-18
forum: Desktop Environments
---

### Post by reuben on 2006-06-18
I have 6 usb ports; two on the back, two on top, and two on my keyboard. When I connect a thumbdrive to the keyboard, it automounts and I get the "whaddya wanna do" dialog; however if I plug it into the top of the computer, it doesn't automount. I know that the usb ports there work...is it possible they're not included in the automount config? How would I diagnose?

---

### Post by Rui Pais on 2006-06-18
hi, 
i'm not sure but seems that i read somewhere that in some cases extra usb ports special on fron side ox computer boxs dont work with new usb 2 drivers/modules but only with the old usb 1.something system and its modules modules. 

Don't know if thats true, but if it is then a basic usb mouse (those that do not require any special module) should work on those ports.

---

### Post by loa on 2007-12-03
I think you have the same problem as I have. My wiring to the front ports are not so good, and only supports usb 1.1. And when Linux tries to initialize the usb 2.0 device, it just silently fails. (You can find some information in the system logs, maybe it was /var/log/syslog). In winxp, the system automatically fallbacks to usb 1.1 in this case, and it would be nice if Ubuntu could do this also. So, I'm pretty sure it is not automount's fault. Does other high-speed devices (like a digital camera or something) work at those front ports, or is it just low-speed devices such as mice or keyboards that works?

You can look at this other thread I just created for more information ([http://ubuntuforums.org/showthread.php?t=630578](http://ubuntuforums.org/showthread.php?t=630578)).

---

