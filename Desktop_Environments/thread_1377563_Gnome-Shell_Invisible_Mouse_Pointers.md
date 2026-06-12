---
title: "Gnome-Shell Invisible Mouse Pointers"
date: 2010-01-10
forum: Desktop Environments
---

### Post by FatalChaos on 2010-01-10
I'm using the latest version of gnome-shell from this ppa: [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing) on karmic. Basically, the mouse pointer seems like it's a layer below the shell, so it dissapears underneath the gnome-shell task bar and activities layer, but all mouse functions still work, I just can't see the damn mouse. There's already been a bug report about this, but I'm wondering if anyone here has managed to have a mouse pointer that doesn't dissapear. [https://bugs.launchpad.net/gnome-shell/+bug/457046](https://bugs.launchpad.net/gnome-shell/+bug/457046)

---

### Post by visionofarun on 2010-01-15
Same issue for me!! Someone help please.

---

### Post by Roasted on 2010-01-15
Same issue...

I also noticed ALT + F2 is gone.

EDIT - Out of curiosity I went to update manager (already updated earlier today) and I saw some mutter updates, so I grabbed them and restarted. When I rebooted, I still had the invisible mouse issue. However, ALT F2 functionality was restored.

Was it the updates?
Was it the reboot? 

I have no idea. But try ALT F2 and type "restart" and see if that helps.

---

### Post by Thomas Garman on 2010-03-05
No mouse pointers when you click on "Activities"....  the mouse disappears, which makes the home folder inaccessible through that set of menus.

---

### Post by Roasted on 2010-03-05
It seems as if my issue was fixed a few weeks ago with an update. Anybody else still having this issue??

---

### Post by saturnblackhole on 2010-03-08
yes im still having this issue, i just setup gnomeshell to be my navtive window manager by using these commands 

> **manoriax said:**
> To make it run natively you have to open a terminal and write:
```
sudo update-alternatives --config x-window-manager

```Select "mutter" there. After this write
```
sudo cp /usr/share/applications/gnome-shell.desktop /etc/xdg/autostart
```hit enter and after a restart say hello to gnome-shell running as native window manager.

and when i restarted i had this mouse problem. any suggestions?

---

### Post by Bubbel on 2010-03-17
Maybe some hints:
It seems to stem from autologin to me. What happens is the first X screen, with the brown startup logo appears, without a mouse pointer in it.
Before it is replaced by my custom background & desktop files etc., I see the gnome-shell bar already present.
This got me thinking: If the mouse cursor is not available during the start of gnome-shell, maybe gnome-shell doesn't recognise it.

What I've done to remedy it was simple. In stead of calling gnome-shell directly from the startup applications, I've made a script:
```
sleep 15
gnome-shell --replace
```

This did it. I saw gnome-shell start after I had my desktop & mouse.
I'm thinking that a delayed, or no autologin would also remedy it.

Hope it helps you all.

Cheers, Bubbel

PS: Fiddle with the sleep timeout a bit. It depends on the speed of your computer, how long the start of gnome-shell should be delayed.

---

### Post by technovir on 2010-05-17
i have still have this problem even after upgrading to lucid. the problem started after i ran an update in jaunty. ever since i've had an invisible mouse after login. recently i installed KDE and discovered that the mouse was not affected in KDE. gnome still had the problem and strangely enough the mouse seemed to return after i started Terminal.
I would greatly appreciate it if someone could tell me how to fix this

---

### Post by verdu on 2010-06-16
> **technovir said:**
> i have still have this problem even after upgrading to lucid. the problem started after i ran an update in jaunty. ever since i've had an invisible mouse after login. recently i installed KDE and discovered that the mouse was not affected in KDE. gnome still had the problem and strangely enough the mouse seemed to return after i started Terminal.
I would greatly appreciate it if someone could tell me how to fix this



try to install proprietary video drivers...
it helped to solve the same problem for me On Ubuntu 10.4

cheers,
Martin

---

