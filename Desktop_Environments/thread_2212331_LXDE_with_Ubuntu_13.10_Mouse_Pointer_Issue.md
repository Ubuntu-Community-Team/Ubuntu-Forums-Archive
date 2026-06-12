---
title: "LXDE with Ubuntu 13.10 Mouse Pointer Issue"
date: 2014-03-20
forum: Desktop Environments
---

### Post by genivasla on 2014-03-20
When i install LXDE desktop environment on a Ubuntu 13.10 server and VNC into the desktop, the mouse pointer is the X crosshair. On earlier versions of Ubuntu this is not the case (it's a normal mouse pointer).

In order to get rid of the X, I have to go to Preferences -> Customize Look and Feel. As soon as the box opens, the X turns into a normal mouse pointer without having to do anything. Problem is I can't seem to get this to "stick." Whenver the VNC is restarted, I have to go through this process again to get the mouse pointer.

I have vnc4server installed, and this is the case regardless of VNC viewer that I've tried so far.

By the way... when I open Customize Look and Feel and toggle over to the Mouse Pointer property, there is nothing listed as an optional theme. Maybe I have to install a theme? Not sure how to do that, but seems odd that the mouse pointer changes automatically.

Anyone know how to make this permanent?

---

### Post by bapoumba on 2014-03-21
Not sure, you may need a desktop, but not sure :)
Please have a look here, posts #3 : [https://bbs.archlinux.org/viewtopic.php?id=56860](https://bbs.archlinux.org/viewtopic.php?id=56860)

Here is mine, which came with the lubuntu-default theme :
```
[Icon Theme]
Inherits=DMZ-White
```

---

### Post by juergen-familiepfeifer on 2014-11-13
I've exactly the same problem with 14.10! Do you have a solution for that?

---

