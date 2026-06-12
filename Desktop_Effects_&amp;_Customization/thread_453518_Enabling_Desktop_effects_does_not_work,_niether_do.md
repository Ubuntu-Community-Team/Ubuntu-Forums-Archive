---
title: "Enabling Desktop effects does not work, niether does the restrictred drivers"
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by Matt_AC on 2007-05-24
Heres my problem.

I have a 8600gts which is only supported by beta drivers at the moment.
When I press the restricted drivers button it just says I don't need them, this is probably because of my video card.

When I try to enable desktop effects the screen goes white....


Anybody know where/how I can get drivers installed. 
I've tried using freeubuntu but I don't know how to configure xorg. :(


Any help appreciated!

---

### Post by blazercist on 2007-05-24
once u have manually installed the driver all you gotta do is 

gksudo gedit /etc/X11/xorg.conf

search for "vesa" and change it to whatever the name of the new driver module is, save and then restart X by doing ctrl+alt+backspace

---

### Post by Matt_AC on 2007-05-24
> **blazercist said:**
> once u have manually installed the driver all you gotta do is 

gksudo gedit /etc/X11/xorg.conf

search for "vesa" and change it to whatever the name of the new driver module is, save and then restart X by doing ctrl+alt+backspace
K, I'll try that.

---

