---
title: "Booting Problem"
date: 2009-04-22
forum: General Help
---

### Post by strikewolf42 on 2009-04-22
Hey everyone, just downloaded Ubuntu from the website and it looked pretty cool.
 
But I have a problem, I installed it from Windows as an alternate OS but when I boot it it gets past the main loading screen, then it looks like its about to display the login window (from my past experience). But instead, it displays a popup that says "Checking for hardware" for a fraction of a second, then the window becomes garbled and nothing more happens.
 
Anyone else have this problem, or know of a way to fix it? I will try to get a screenshot in a minute.
 
Thanks!

---

### Post by spiderbatdad on 2009-04-22
It seems like a video card requiring a proprietary driver is in use. Some of these can be installed after boot...er lol.

Possibly a boot option like "xforcevesa" will work from the grub menu...or acpi=off. Maybe recovery offers a failsafe graphics boot? A little tricky if you cant get to the login screen to choose failsafe gnome.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by strikewolf42 on 2009-04-22
Got a better glimpse at the window, it said Checking Installation rather than Checking Hardware. 
 
Also, I got a screenshot of it. Sorry for bad quality had to take it with my phone.
 
[http://img394.imageshack.us/img394/4931/0422091743.jpg](http://img394.imageshack.us/img394/4931/0422091743.jpg)

---

### Post by spiderbatdad on 2009-04-22
yeah that looks like a video card issue. I think the right boot options will get you going, but they can require a little trial and error. Maybe consider burning a jaunty beta cd? Though you may still require the right boot options. The link above explains boot options and how to apply. Make them permanent by editing /boot/grub/menu.lst

---

### Post by strikewolf42 on 2009-04-22
Alright thanks, I'll try these!
 
Will report with results.

---

