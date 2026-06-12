---
title: "How do I replace metacity with WindowMaker without ditching the rest of GNOME?"
date: 2010-07-09
forum: Desktop Environments
---

### Post by Dthdealer on 2010-07-09
I'm a lover of Window Maker, but I have stopped using it for several months due to the love of the ease of use of the Gnome Environment.  Supposedly I can swap out Metacity with Window Maker and I have attempted to do so according to the instructions at [http://ubuntuforums.org/showthread.php?t=1105582]("http://ubuntuforums.org/showthread.php?t=1105582")
> **mcduck said:**
> To change the window manager in Gnome open Gconf-editor (hit Alt-F2 and run "gconf-editor). Then browse to desktop/gnome/sesssion/required_components and change the valune of "windowmanager" to wha ever you want to use.
> **rick71 said:**
> I think I have been able to replace Metacity with WindowMaker. IN gconf-editor: desktop/gnome/applications/window_manger I have put /usr/bin/wmaker in both current and default. So far, WindowMaker starts as the default window manager.

Now when I log in through GDM using the gnome session no WM at all starts.  Where can I access the error logs?  Currently I have to start Metacity in a terminal.  Wmaker works here too but it spams gnome-bar window-list with an infinite amount of non-existent windows, something else I need help with.

You may think I am crazy to want to use anther window manager *in* the Gnome environment when I could just choose it at GDM ( or in my .xinit file like I used to have things setup without GDM ).  The problem is the allure of automatic printer configuration and the gnome-bar among other things ( I can turn the tile functionality of Wmaker off ) is only replaceable with manual configuration. On the other hand the compositing feature of Metacity brings a *horrid* window and menu drop-shadow, but when I turn it off I get ugly vsync distortion when moving windows around.

Compiz ( fusion? ) fixes that problem with its configurability, but it ignores my configuration to have alt+rightclick resize windows rather than bring up their menu and also makes my desktop Vista-ish ( yuck! ) even with extensive ccsm configuration. 

So is the window manager treated as a module that can be replaced in Gnome or must I escape the Gnome environment to use another?

Thanks in advance

EDIT: Now that I am using Metacity via the terminal ( although I could change the gconf settings back ) I can see any messages it prints.  This one has a sense of humour - I'm reincoding a video ( output gddd.avi ) using ffmpeg so that I can play it on the tv ( it is currently flv ).
```
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x4200003 (gddd.avi); these messages lack timestamps and therefore suck.
```

---

### Post by Dthdealer on 2010-07-10
Found solution

[http://ubuntuforums.org/showthread.php?t=490376]("http://ubuntuforums.org/showthread.php?t=490376")

---

