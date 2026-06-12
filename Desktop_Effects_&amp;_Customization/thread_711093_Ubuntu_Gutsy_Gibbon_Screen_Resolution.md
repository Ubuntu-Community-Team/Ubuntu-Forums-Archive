---
title: "Ubuntu Gutsy Gibbon Screen Resolution"
date: 2008-02-29
forum: Desktop Effects &amp; Customization
---

### Post by aditiudupa on 2008-02-29
My Laptop is an IBM R51. My Resolution is 1024x768. I want it to be at least 1200x800. Is it possible to change it to that? In System>Preferences>Screen Resolution, 1024x768 was the highest i got. I even tried 'sudo dpkg-reconfigure xserver-xorg', but when i restarted,  1024x768 was the highest i could chose. Thanks in advance

---

### Post by mapes12 on 2008-02-29
I had a similar problem. I reinstalled Ubuntu from the Alternate CD and changed the resolution (F4 I recall) at the first screen. When the install completed I was then in the resolution I needed for my Thinkpad T23.

---

### Post by XuJamie on 2008-02-29
you could try editing the xorg.conf file to enable the higher resolution. I had to change mine from 24bit to 16bit to enable the 1024x768 res (i was restricted to 800x600 previously). 

This can be done on the terminal by typing 'sudo mousepad /etc/X11/xorg.conf'

and changing the Depth under the screen section. If yours is currently 24 then try 16. If its currently 16 then try 8.

P.S if you dont have the mousepad texteditor, replace 'mousepad' with whatever app you have installed for this. (nano, vi, etc)

Hope this helps
Jamie

---

