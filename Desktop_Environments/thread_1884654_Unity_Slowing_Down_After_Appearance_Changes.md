---
title: "Unity Slowing Down After Appearance Changes"
date: 2011-11-21
forum: Desktop Environments
---

### Post by jal4568 on 2011-11-21
Hello, I've run into a reoccurring problem with my 11.04 Unity install and haven't found anyone else in the forums discussing it so I thought I'd post it. 

Basically, my 11.04 desktop grinds to a screeching halt if I change the Appearance of the desktop via the "Appearance Preferences" window. 

My install will become very slow & buggy after such an appearance change. Applications crash, launcher icons take forever to open, the terminal will show up as a blank window, the alt-tab switcher is VERY slow, etc. It will correct after a reboot but previous versions of Ubuntu never needed a **reboot** to function after an appearance change.

As a check, I've rebooted & then opened the Appearance change window first, play around & then try to work. The result is a very SLOW and frustrating experience. So something about changing the Appearance settings is slowing everything down by screwing up the desktop. 

Does anyone have any ideas about what could be causing this or how I could minimize this problem in the future?

---

### Post by jimmydean886-2 on 2011-11-21
Try running the appearance preferences through the command line, and post the output. That would help greatly. I personally haven't used Natty since August, so I am not familiar with that command, but I know that it's out there, because I used to use it on occasion.

you never know, maybe you'll find something intelligable in all of that output. Good luck!

--jimmydean886-2--

---

### Post by jal4568 on 2011-11-21
Hmmmmm, the command line option did do something interesting....it appears that Ubuntu is looking for a theme engine that I no longer have installed. 

```
(gnome-appearance-properties:3197): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",
```

This is repeated several times. I can't find any evidence of this theme but at least I have a lead now. Thanks for the help!

---

