---
title: "Change color depth?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Donnut on 2005-11-03
Well, i finally figured out how to install my ATI video drivers, but one thing I don't know is how to change color depth to 16-bit instead of 24-bit.  I tried manually editing the text file I get with the command sudo gedit /etc/X11/xorg.conf, but I must have done it wrong 'cause I got a blank-white screen on restart.  How do I do this?

---

### Post by Ampersand on 2005-11-03
If you open a terminal and run 
```
sudo dpkg-reconfigure xserver-xorg
```
you'll be able to set what resolutions/colour depths are available.

---

### Post by Donnut on 2005-11-03
Which driver should i chose? fglrx or ati?

---

### Post by Donnut on 2005-11-04
OK, is there any other way to change depth?  Can I do it manually?  I tried both ati and fglrx, and both times I got a blank screen that slowly changes to white....

---

