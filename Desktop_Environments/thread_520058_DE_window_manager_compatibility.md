---
title: "DE window manager compatibility?"
date: 2007-08-07
forum: Desktop Environments
---

### Post by dbunder on 2007-08-07
I haven't really used any sort of linux since the introduction of desktop environments (gnome, xfce, kde).  I used to use blackbox and was quite happy with it.

But desktop environments, as weird as they are to use, do have their advantages.  Problem is, I despise the default managers for the three aforementioned desktop environments.  I'd like to use something else.

I remember back in the day, blackbox had minor KDE and gnome compatibility.  You could run blackbox as your window manager for either, though it was kind of shoddy.  I've been looking for window manger compatibility with desktop environments on google and these forums, and can't find a lot.  Are there any resources to tell me what I can use with what?  I'm most interested in using fluxbox or openbox on top of xfce, or if I'm really desperate, KDE.  No gnome for me - I've never encountered a desktop environment, in any operating system, that slowed my work and play down so much (or made me wish I was blind, heh heh).

Thanks for any help!

---

### Post by merlinus on 2007-08-07
Do a search for fluxbox and you will find all sorts of good ideas, tips, etc.

Also, fluxbuntu has resources including a forum:

[http://community.fluxbuntu.org/](http://community.fluxbuntu.org/)

-merlin

---

### Post by fistfullofroses on 2007-08-07
I used to use evilwm with gnome. There was a how to on it for a while. No idea with xfce. You could check your xfce4.desktop file. Just look for a line that contains xfwm4 and change it out to fluxbox.

---

### Post by urukrama on 2007-08-08
To have KDE with Openbox, install the[ latest version of Openbox]("http://icculus.org/openbox/index.php/Openbox:Download"), log out, and select 'KDE/Openbox' in your login screen (under 'Sessions'). It is that simple.

XFCE with Openbox is a little harder, but doable. Install Openbox, and then execute the following command (make sure you are logged into xfce!):

```
killall xfwm4
```

Or if you also want to give Openbox control over the desktop (meaning you don't have any icons on it, but can use the right and middle click Openbox menus, instead of the Xfce ones), do the following:

```
killall xfwm4 xfdesktop
```

This kills the window manager of xfce (xfwm4) and the desktop (xfdesktop).

Now you'll have to load Openbox:
```
openbox --replace
```
Openbox will now be running inside xfce. To change these settings, save your session when you log out, and xfce will load openbox again next time you log in. (In theory, you should be able to do this with any other wm, but I've never tried it).

Alternatively, you could just use a regular plain Openbox session, and add whatever xfce or KDE components you want to your /home/username/.config/openbox/autostart.sh file.

---

