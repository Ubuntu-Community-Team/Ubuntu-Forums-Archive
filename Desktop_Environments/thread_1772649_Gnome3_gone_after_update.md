---
title: "Gnome3 gone after update"
date: 2011-05-31
forum: Desktop Environments
---

### Post by CodeRage on 2011-05-31
This is for folks like me who have the following:

Ubuntu 11.04 Natty Narwhal
Gnome 3 (gnome-shell replacing Unity)
Nvidia binary driver (270.41.06 more or less)
No patience for your beloved Gnome 3 desktop environment to go away on updates.


Here is what I found after the last update: My gnome-shell went away and I went to fallback gnome with panels. I didn't like this one bit so after some tinkering around, here is the 'simple' solution I found to resolve it. Since I have a binary nvidia driver installed, I reinstalled it by going into console (ctrl + alt + f2), typing ```
 sudo service gdm stop 
``` then changing directory to where your nvidia binary driver was downloaded to, then typing ```
 sudo sh NVIDIA-Linux-x86_64-270.41.06.run 
``` (that's the version of the file I had downloaded from nvidia specifically for 64bit Ubuntu 11.04). Once you go through the install (assuming it went like you know it should), then you can do ```
 sudo service gdm start 
``` and once you log back in via gdm login, you should be fine (if and only if the gnome3 loading issue went to fallback mode because of improper hooks to video driver or whatever it is). 

I hope this helps some folks who deal with this like I do.

---

