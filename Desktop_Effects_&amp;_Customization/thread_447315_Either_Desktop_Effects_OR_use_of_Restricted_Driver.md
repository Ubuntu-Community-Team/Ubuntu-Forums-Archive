---
title: "Either Desktop Effects OR use of Restricted Drivers. Why not Both?"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by hanzj on 2007-05-17
Hello, I can have Desktop Effects (cubic desktop, warble) enabled. But when I turn on restricted drivers, Desktop Effects are disabled. Why?

By the way, nothing looks different now that I have my ATI driver enabled. What's the use of "Use restricted Drivers"?

---

### Post by kahping on 2007-05-19
The closed source (restricted) ATi drivers don't support the required extensions to allow Desktop effects to work.

For the time being it's either desktop effects, or closed source drivers. You can't have both. Hopefully this'll change in the near future, but this depends on ATi (or should i say AMD?)

---

### Post by Soybean on 2007-05-19
> **hanzj said:**
> What's the use of "Use restricted Drivers"?
If everything you want to do is working fine without them, then they have no use. :) They provide 3d acceleration for some video cards that the open source drivers don't work as well with. If you are trying to use some 3d program that doesn't seem to be working very well, try switching to the restricted drivers... otherwise, I wouldn't worry about them.

---

### Post by hanzj on 2007-05-22
The waggle of the borders work, but I can't get the cubic desktop thingy to work. How do we do it?

---

### Post by ronocdh on 2007-05-22
> **kahping said:**
> The closed source (restricted) ATi drivers don't support the required extensions to allow Desktop effects to work.

For the time being it's either desktop effects, or closed source drivers. You can't have both. Hopefully this'll change in the near future, but this depends on ATi (or should i say AMD?)
This is just plain false. I have Beryl working perfectly with the fglrx (proprietary ATI driver), although it did take a [certain amount of setup]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m").

Good luck guys, and post back with your luck.

---

### Post by cstrippie on 2007-05-22
ATI closed-source requires XGL to handle a compositing desktop.  To be of any assistance, I would need to know what vidcard you're using - if open source radeon drivers are working properly, I'd just stick with them absent a specific need radeon doesn't meet.

---

### Post by hanzj on 2007-05-23
To get the cubic desktop to work, I installed compiz manager. That put GL desktop under the System menu.

---

