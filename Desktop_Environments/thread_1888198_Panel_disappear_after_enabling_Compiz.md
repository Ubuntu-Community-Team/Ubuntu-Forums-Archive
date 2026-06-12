---
title: "Panel disappear after enabling Compiz"
date: 2011-11-28
forum: Desktop Environments
---

### Post by new123 on 2011-11-28
[11.10] Whenever I enable Compiz, my panel just disappear and when I change some of settings, even the window border disappear.
I have worked with Compiz with no such problem b4 I formated and reinstalled Lubuntu, but now I don't know why not work, I tryied with making Compiz settings all default, nothing changed. :rolleyes:

---

### Post by Lastguest on 2011-11-28
i had the same issue but being a noob i re installed ubuntu and up to now i have only used compiz to reduce the size of the side menu with no ill effects but before when i unticked the wall it went txts up

i als tried the terminal to reset to no avail. hope u get sorted

---

### Post by new123 on 2011-11-28
I fix it _only if I set Compiz as my default Window manager_:
edit /home/yourusername/.config/lxsession/Lubuntu/desktop.conf and set the window manager to compiz:

```
[Session]
window_manager=compiz
```When I reboot, it loads automaticaly and I enabled Wobbly Windows, 3dCube etc. and it works with no problem..

---

### Post by joelorenzo on 2011-11-29
i have the same sort of issue with ubuntu 11.10. still trying to work it out, but yes, i also was using compiz when my app launcher failed. now i dont know what to do :|

---

### Post by jimav on 2011-11-30
Killing & restaring lxpanel seems to make the panel re-appear.

Sounds like a race condition somewhere...

---

### Post by joelorenzo on 2011-11-30
> **jimav said:**
> Killing & restaring lxpanel seems to make the panel re-appear.

Sounds like a race condition somewhere...

i am a total noob. how does one go about doing what you suggested?

---

### Post by new123 on 2011-12-01
> **jimav said:**
> Killing & restaring lxpanel seems to make the panel re-appear.

Sounds like a race condition somewhere...

This works, thanks :)

---

### Post by new123 on 2011-12-01
> **joelorenzo said:**
> i am a total noob. how does one go about doing what you suggested?
To kill it (in Lubuntu), go LXTerminal -> lxtask -> find lxpanel -> Right click -> Kill, then, (in LXTerminal) type lxpanel to re-start the panel and it will appear, I just tested it, works fine.

Edit: After typing 'lxpanel' in terminal, maybe it will load some different panel (a bit ugly lol) and for sure, if you customised ur panel before, ur customs will not be loaded so, instead of only typing 'lxpanel', type 'lxpanel --profile Lubuntu'.

---

