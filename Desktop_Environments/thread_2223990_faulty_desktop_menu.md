---
title: "faulty desktop menu"
date: 2014-05-14
forum: Desktop Environments
---

### Post by Jim_Van_Horn on 2014-05-14
Transitioning from very old desktop computer [Kubuntu 14.04] to mildly old laptop [HP G60, Lubuntu 14.04].  So far, learning/customizing the new environment has been pretty smooth, but I'm not figuring out how to fix this desktop menu.

Right-click on the desktop brings up a menu selection.  Some of the menu items launch apps correctly ("File Manager", "Terminal"), but most of them fail and throw me out of my session (i.e. I have to log back in).

I've learned how to disable the menu [Lubuntu menu -> Preferences -> Desktop Preferences -> Advanced (tab) -> "Show menus provided by window managers when desktop is clicked" (check/uncheck)] but I'd prefer to fix it rather than abandon it.  I've been looking for a way to configure that menu, but I haven't found it yet.

-jvh

---

### Post by ibjsb4 on 2014-05-14
This is odd behavior.  First, verify the session you are on.
```
echo "$XDG_CURRENT_DESKTOP"
```Have you tried to open broke app's in terminal?

also

Go to /usr/share/applications and try starting apps from there.

---

### Post by vasa1 on 2014-05-14
> **Jim_Van_Horn said:**
> ...
Right-click on the desktop brings up a menu selection.  Some of the menu items launch apps correctly ("File Manager", "Terminal"), but most of them fail **and throw me out of my session** (i.e. I have to log back in).
...
I can understand some or most of them failing but the part in bold is very unusual.

Can you put up the output of *ls -l ~/.config/openbox* for a start?

And, if you know how to take a delayed screenshot could you provide the image of what you see when you right-click on the desktop?

---

### Post by Jim_Van_Horn on 2014-05-15
OK, I've done some more research.  Here's what I've found.

I went to [FONT=courier new]~/.config/openbox/lubuntu-rc.xml[/FONT] (thanks vasa1), which lead me to [FONT=courier new]/usr/share/lubuntu/openbox/menu.xml[/FONT] (now I know how the menu is constructed/organized), which lead me to [FONT=courier new]/usr/bin/lxsession-default[/FONT].

From the command line I'm able to launch the same apps that are successful from the desktop menu.
```
dbus-send --session --print-reply --dest="org.lxde.SessionManager" /org/lxde/SessionManager org.lxde.SessionManager.SessionLaunch string:"**terminal_manager**" string:$PWD
```
This works fine.

But the menu selections that fail, also fail from the command line.
```
dbus-send --session --print-reply --dest="org.lxde.SessionManager" /org/lxde/SessionManager org.lxde.SessionManager.SessionLaunch string:"**calculator**" string:''
```
This creates the output:```
Error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```
This is logged in [FONT=courier new]~/.xsession-errors[/FONT]:
```
init: lxsession main process (23145) killed by SEGV signal
init: Disconnected from notified D-Bus bus
```

My session is terminated and I have to log in and start all over.

Alas, D-Bus is somewhat new territory for me so I'm not sure where to go from here.  Any thoughts?

-jvh

---

### Post by vasa1 on 2014-05-15
I've never come across this dbus way of launching programs!

---

