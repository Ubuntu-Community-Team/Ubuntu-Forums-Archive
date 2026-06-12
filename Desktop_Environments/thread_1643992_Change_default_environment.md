---
title: "Change default environment"
date: 2010-12-12
forum: Desktop Environments
---

### Post by PHANTOM X on 2010-12-12
I need some help on changing my desktop to ICEWM. Want my laptop to run light as possible by using thunar, icewm panels and themes. I got it to change to ICEWM as the default window manager instead of compiz, but can't figure out how to change the panels, themes and file manager?

---

### Post by 3Miro on 2010-12-12
Right now you have Gnome + IceWM. You want IceWM as its own standalone environment.

Try logout -> select IceWM from the bottom menu for the current session and then login. There may be an extra step to force it to remember the new selection as default, but I think it will remember it.

---

### Post by PHANTOM X on 2010-12-12
I want it to be forced. :) Unfortunately after I logged in no panel was visible. I also use a wireless connection, but the network applet doesn't show or work forcing me to use an ethernet connection. :(

---

### Post by 3Miro on 2010-12-12
> **PHANTOM X said:**
> I want it to be forced. :) Unfortunately after I logged in no panel was visible. I also use a wireless connection, but the network applet doesn't show or work forcing me to use an ethernet connection. :(

The panel should hold a "notification" applet that in its turn holds nm-applet, which controls NetworkManager, which is exactly what it says it is. In that way nm-applet is independent from the desktop environment (Gnome, XFCE, LXDE) and NetworkManager doesn't even need graphical environment, it can be controlled via a terminal.

Why the IceWM panel doesn't show up, I don't know. I didn't even know IceWM even has a panel of its own.

---

### Post by PHANTOM X on 2010-12-12
ICEWM doesn't have a panel. I installed ltpanel. How do I connect via the terminal?

I did something that caused it to show up. Possibly installed something in the software center.

Edit: It seems it was the "GNOME support files for IceWM" that enabled the panel.

---

### Post by 3Miro on 2010-12-12
Most standalone window managers have a right-click then menu option. If you right-click on the desktop, you should be able to get to a menu. From there, you can open any program that you want.

If you want the panel, you will have to call it on startup, however, I don't know how to call a startup application in IceWM.

Note: You can try to start the panel from the terminal (type ltpanel or something like that), or you may also be able to call programs if you press Alt + F2.

---

### Post by dxtan3 on 2010-12-12
Hi, I'm very new here and this is my first post. Sorry if this is the wrong thread. . what is the difference between ICEWM and Xfce?

---

### Post by roguebuck on 2010-12-12
IceWM is a standalone window manager, while Xfce is a full desktop environment.

check [xwinman.org]("http://xwinman.org")

---

### Post by PHANTOM X on 2010-12-13
Yeah I noticed that you can right click and get access to the menus. :) I would do a command line install if I didn't use wubi now and like it as it's easy to remove and reinstall. :) Guess this'll work for now with icewm instead of compiz. :)

---

