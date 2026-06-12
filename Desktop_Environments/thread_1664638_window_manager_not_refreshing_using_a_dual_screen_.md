---
title: "window manager not refreshing using a dual screen setup"
date: 2011-01-11
forum: Desktop Environments
---

### Post by oneindelijk on 2011-01-11
Hi, 

I have Ubuntu 10.10 on an Acer Travelmate 5520 (which has the ATI Xpress 1250).
I'm using a second screen at 1440x900 and the laptop has 1280x800.

Mostly it's working fine, but sometimes the menus appear blank or they stay on the screen after the focus is lost.

Sometimes I can solve that by running compiz (which causes the system to re-initiate the fallback window manager (that would be metacity ?).
Compiz isn't working anymore since I connected this second screen, not even in single screen mode.
This is the error it throws
```
compiz                                                  ~
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x5800046 (Ubuntu For)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x5800046 (Ubuntu For); these messages lack timestamps and therefore suck.
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x5800046 (Ubuntu For); these messages lack timestamps and therefore suck.
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x5800046 (Ubuntu For); these messages lack timestamps and therefore suck.

```
How can I enable compiz on this dual screen layout
or is there a fix for metacity ?

---

### Post by oneindelijk on 2011-01-13
Bump
I noticed that there is actually two problems (or two symptoms coming from one problem)
One is that the menus (from gnome and gtk-apps) are not properly losing their focus. The rectangle(s) of some menus stays on the screen until I give focus to that particular menu or submenu again and then fold the same way I unfolded it (in case of submenus) and make the active application have the focus. If I to click on another application the last menu stays on the screen, on top of everything else.

The second issue is that the menus aren't properly drawn, I have to give focus several times before they shown their contents and combined with issue 1, described above, sometimes the menu leaves a black square on my screen)

---

### Post by oneindelijk on 2011-01-13
Just an idea...
Could it be related to something with D-Bus ?

---

