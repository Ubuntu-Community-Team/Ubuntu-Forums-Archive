---
title: "Desktop contents, panels disappear"
date: 2009-09-10
forum: Desktop Environments
---

### Post by Psyrus on 2009-09-10
I've recently installed Jaunty on my machine and a day or two ago I began having a problem with the desktop environment. It may have been a change in the configuration somewhere(I am using Compiz)...I can't remember making any radical changes.

Essentially, whenever I use the short-cut keys [ctrl][alt][shift]+arrow to change to another desktop, all my panels disappear. Mounted drives are not shown on the desktop, although the desktop image is shown. I can exit the system through [alt][ctrl][del], and can run applications from the [alt]-F2 run box. I've tried to start the panels again using [alt]-F2 but this doesn't work. Does this have something to do with X?

---

### Post by hellblazer on 2009-09-10
Hmm, it sounds like Compiz or your display drivers are freaking out. Try turning off Compiz by right clicking on the desktop and going to the Visual Effects tab. Select None. If you're still having the problem then Compiz is not to blame and you can try trouble shooting your graphics drivers.

If you think it's X, you can try restarting it by running the terminal command:
```
sudo etc/init.d/gdm restart
```

Not really a solution, but it's somewhere to start.

---

### Post by mcduck on 2009-09-10
Check your Compiz configuration, and make sure you have the number of desktops set to 1.

To adjust the amount of virtual desktops you need to use horizontal & vertical virtual sizes. Increasing the actual number of desktops creates you a completely new desktop, and the panels and other stuff, by default, only runs on the first desktop.

So if you want a cube with four sides you set the horizontal virtual size to 4, vertical to 1 and number of desktops to 2. Then increasing the number of desktops would create another, completely separate cube with another virtual desktops..

(If you actually want more cubes instead of virtual desktops you'll have to create new panels for each new desktop, and use gconf-editor to assign those panels to the new desktop)

(By the way, the Run dialog opened by pressing Alt-F2 in Gnome is a feature of Gnome-Panel, so it won't work if you have no panels..)

---

### Post by Psyrus on 2009-09-11
Thanks for the suggestions. I went back and checked and changed all my desktop settings to 1 desktop. Have now expanded back to 4 virtual desktops. I think the issue arose because I had 4 desktops as well as 4 virtual desktops. Is my reasoning correct?

---

### Post by mcduck on 2009-09-11
> **Psyrus said:**
> Thanks for the suggestions. I went back and checked and changed all my desktop settings to 1 desktop. Have now expanded back to 4 virtual desktops. I think the issue arose because I had 4 desktops as well as 4 virtual desktops. Is my reasoning correct?

Yes, that's correct. Desktops and virtual desktops are different things..

---

### Post by Psyrus on 2009-09-11
Great. Thanks for the help!

---

