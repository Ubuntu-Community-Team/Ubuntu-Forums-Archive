---
title: "Cannot switch active window after login"
date: 2010-02-09
forum: Desktop Environments
---

### Post by acron on 2010-02-09
Hi there,

I've a strange problem. After login I can start applications e.g. Firefox or Evolution, but than after some seconds I cannot focus another window, neither by a mouse click nor using Alt-Tab. I can start a Terminal with Ctrl-Alt-t (which I set as a shortcut before).
When I restart gnome (I use "sudo /etc/init.d/gdm restart" in the terminal) everything works fine until the next boot.
I already disabled the desktop effects but without any luck.
I'm currently running low on free hard disk space and ubuntu keeps warning me about that but there is still ~400MB free space left, so that shouldn't be a problem, right?

Any help with this one is highly appreciated! 

Greets acron

---

### Post by pritamps on 2010-02-09
Try running nautilus from a terminal

```
nautilus &
```

It seems to me like nautilus is not starting for you.

---

### Post by acron on 2010-02-10
> **pritamps said:**
> Try running nautilus from a terminal

```
nautilus &
```

It seems to me like nautilus is not starting for you.

thanks for your reply. Sadly starting nautilus does not help. It prints 
```
Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
```
and opens a nautilus-window of my home which then has the focus. But still I cannot focus any other window. I also get the above error message if I restart the gnome session which then works and run nautilus from a terminal. The message seems to come from bug [#454234]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234"). 

I found some strange errors in /var/log/gdm/:0-greeter.log which may be related to the problem.

```
(gnome-settings-daemon:3014): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3014): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Warnung der Fensterverwaltung: Gespeicherte Sitzungsdatei /var/lib/gdm/.config/metacity/sessions/10b4269780fee569be12657955566347500000030090001.ms konnte nicht gelesen werden: Datei »/var/lib/gdm/.config/metacity/sessions/10b4269780fee569be12657955566347500000030090001.ms« konnte nicht geöffnet werden: No such file or directory
** (process:3024): DEBUG: Greeter session pid=3024 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-VbGgSU/database
Warnung der Fensterverwaltung: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400027 (Anmeldefen)
Warnung der Fensterverwaltung: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Warnung der Fensterverwaltung: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400027 (Anmeldefen)
Warnung der Fensterverwaltung: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Warnung der Fensterverwaltung: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400027 (Anmeldefen)
Warnung der Fensterverwaltung: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Warnung der Fensterverwaltung: CurrentTime used to choose focus window; focus window may not be correct.
: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

```
[INDENT]FYI: Some of the messages are german, sorry.
[COLOR="Red"]"Warnung der Fensterverwaltung"[/COLOR]
translates to 
[COLOR="SeaGreen"]"Warning of the window manager"[/COLOR] 
and 
[COLOR="Red"]"Gespeicherte Sitzungsdatei X konnte nicht gelesen werden: Datei »X« konnte nicht geöffnet werden"[/COLOR]
translates to 
"[COLOR="SeaGreen"]Saved session file X could not be read: File »X« could not be opened"[/COLOR]
(IMHO it's a rather stupid idea to localise log messages but anyway)
[/INDENT]
Can someone tell me where the information about the gnome session to load is stored?

Greets acron

---

### Post by jieter on 2010-02-10
Same here on Karmic Koala, fully updated.

 - Mouse sometimes does not work on windows. (it does work for the gnome-panel)
 - Sometimes the mouse works on the window below the active one.

Restarting GDM like stated above fixes the problem only for a while. While in the broken state, 'switching windows' is possible by closing the active one, the window which was active before is activated.

some searches in launchpad for this bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)
[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/505494](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/505494)

---

### Post by acron on 2010-02-10
> **jieter said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)
[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/505494](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/505494)
This bugs seem not be related to *my* problem as it is said that keyboard shortcuts are still functional, but I cannot switch the active window with Alt-Tab.

---

### Post by acron on 2010-02-22
*bump*

Sorry for bumping but I'm really lost here :confused:

---

