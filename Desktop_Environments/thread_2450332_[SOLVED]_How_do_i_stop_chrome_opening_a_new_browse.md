---
title: "[SOLVED] How do i stop chrome opening a new browser window for my browser tabs ... ?"
date: 2020-09-11
forum: Desktop Environments
---

### Post by dbee on 2020-09-11
This happens to me all the time. I'm clicking on one of the chrome tabs on gnome in ubuntu and it opens a new browser window. Pain in the a**.

How do I stop this from happening ? Also is there a shortcut to switching between open applications on desktop ?

---

### Post by drpjkurian on 2020-09-11
> **dbee said:**
> 
How do I stop this from happening ? Also is there a shortcut to switching between open applications on desktop ?

You may use the key combination of Alt-Tab to switch between the open application on the desktop.

---

### Post by dbee on 2020-09-20
Thanks drpjkurian

how do i stop my tabs from opening on a new window though ?

---

### Post by TheFu on 2020-09-20
I cannot help with chrome. Won't allow that software on my systems. Ever. But a guess would be if the XDG_OPEN variable isn't set correctly, that would be my first guess and place to look.  If Chrome is like Chromimum, then it is distributed as a snap package. Those run inside a sandbox, so it may not be possible to pass "open" URL requests from outside processes. I don't know.  The *Ubuntu desktop guide* should have steps, if any are needed, to change the default browser from whatever it is on your desktop to google's chrome. On mine, firefox was installed as the default. 
[https://help.ubuntu.com/stable/ubuntu-help/net-default-browser.html](https://help.ubuntu.com/stable/ubuntu-help/net-default-browser.html) seems relevant. IDK. Google found it.
[LIST=1]
[*]    Open the Activities overview and start typing Details.
[*]    Click on Details to open the panel.
[*]    Choose Default Applications from the list on the left side of the window.
[*]    Choose which web browser you would like to open links by changing the Web option.
[/LIST]

Switching between applications is a function of the window-manager, WM. What and how that can be accomplished depends completely on the WM use and configuration of it.  

For example, my WM will show a list of all running applications if I right click anywhere on the desktop. I'm using fvwm.  If I want to toggle forward through the list of applications, <alt>-tab can be used. To go backwards in that list, <shift>-<alt>-tab works.  Openbox, another WM, works the same way with default settings.

If you are running the default Ubuntu Desktop, then you have Gnome3 and the WM is mutter (I think).  For a guide as to how that works, google "ubuntu desktop guide".  There are also lots and lots of videos online for this stuff. Those videos will probably concentrate on the more hidden techniques. <alt>-tab is pretty standard across all OSes.

---

