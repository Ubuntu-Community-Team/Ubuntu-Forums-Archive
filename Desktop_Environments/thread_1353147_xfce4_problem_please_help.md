---
title: "xfce4 problem please help"
date: 2009-12-12
forum: Desktop Environments
---

### Post by deankovell on 2009-12-12
I screwed up xfce. I was changing backgrounds and stuff, and something I did put the default gnome background over my wallpaper. Then I turned on desktop effects and it installed the propriatary nvidia graphics driver. when I rebooted all I got was the default gnome background with thunar opened. There aren't any visible panels . I can't move the Thunar window. I can resize it and navigate through folders and stuff. I can start programs from the icons in /usr/bin. There's no buttons for closing any of the windows I open up, but I have the menu items like File, edit, view, history, bookmarks, etc. 
   Right now I have firefox open, and I can see the filemanager open behind it, but if I click on it, it won't bring it to the top. 
If someone could point me in the direction of what to be looking up to fix this, I would appreciate it. Thanks

---

### Post by Simian Man on 2009-12-12
It sounds like your window manager and panel are not running.  To diagnose why, open a terminal and type:

```
xfwm4 &
```

To launch the window manager.  That should either give you the ability to move and focus windows, or give you some error output.

To figure out what's wrong with your panels, type:

```
xfce4-panel &
```

Likewise that should either restore your panels or give you some errors.

---

### Post by deankovell on 2009-12-12
Thanks simian man,
 It took two seconds with your help and now everything's all working. Thanks for your time and quick reply.

---

