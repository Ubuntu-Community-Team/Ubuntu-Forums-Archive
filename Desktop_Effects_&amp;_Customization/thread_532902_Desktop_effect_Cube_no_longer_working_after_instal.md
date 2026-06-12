---
title: "Desktop effect Cube no longer working after installing VMWare Tools (in VMWare Server"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by DerridaIsDead on 2007-08-23
Hey there,
I've installed VMWare Server and created a Windows XP Professional Virtual Machine.
After bootup of XP in VMWare, I installed VMWare Tools and noticed that since then, the Cube desktop effect in Feisty was no longer working. (Wobbly effect still working though.)

Anyone had this experience before?
Solutions?

Thanks...

---

### Post by praet on 2007-08-23
No problems here.
It may be that you are trying to use keyboard mapping that is locked by vmware when you are in a session (Ctrl+Alt).  

If you click on a workspace does the cube rotate to it?
I would check that cube plugin and cube rotate are enabled in compiz config.

---

### Post by DerridaIsDead on 2007-08-24
Thanks for your reaction praet
Everything in gconf-editor seemed fine. Active-plugins looking OK.

Don't laugh, I've just discoverd the gnome-compiz-preferences app. (Can only start it through command line though.) It seems that the number of viewports was simply reduced to 1. God knows why. 
Changed it to 4 and had my cube-feeling back.
Boy, do I need to learn a lotta stuff...
Thanks anyway.

---

### Post by praet on 2007-08-27
Great!

---

