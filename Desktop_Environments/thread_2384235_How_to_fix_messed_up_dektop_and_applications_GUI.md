---
title: "How to fix messed up dektop and applications GUI?"
date: 2018-02-04
forum: Desktop Environments
---

### Post by f(fanta) on 2018-02-04
Windows in my desktop now have missing or odd elements. See for instance the screenshot below: no tab separators, buttons are not drawn (Revert, Close), a white box around the System Settings icons.
How can I restore the desktop/GUI appearance to the default without reinstalling Ubuntu? 
It started right after I installed Evolution and Geary e-mail clients.
**Running Ubuntu 16.04 with Unity.**

In /var/log/syslog there is a long list of messages related to Gtk, like:

```
Feb  4 13:43:16 Count-Zero gnome-session[4503]: (unity-control-center:5650): Gtk-WARNING **: Theme parsing error: gtk-widgets-borders.css:31:18: The :insensitive pseudo-class is deprecated. Use :disabled instead.
...
Feb  4 13:43:31 Count-Zero gnome-session[4503]: gnome-session-binary[4503]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
...
Feb  4 14:06:45 Count-Zero org.gnome.Terminal[4367]: (gnome-terminal-server:5913): Gtk-WARNING **: Theme parsing error: gtk-widgets-borders.css:31:18: The :insensitive pseudo-class is deprecated. Use :disabled instead.

```

Here some things I tried so far:


[LIST]
[*]purge Evolution and Geary 
[*]purge and reinstall ubuntu-desktop (from console, CTRL+ALT+F1) 
[*]purge and reinstall unity (from console, CTRL+ALT+F1) 
[*]rm  -rf ~/.compiz-1 ~/.config/compiz-1 
[/LIST]


[ATTACH=CONFIG]278435[/ATTACH]

---

### Post by TheFu on 2018-02-04
Create a new userid.  Use it and slowly migrate over files and settings from the old account.

---

### Post by f(fanta) on 2018-02-04
> **TheFu said:**
> Create a new userid.  Use it and slowly migrate over files and settings from the old account.

The new user has the same issue.

---

### Post by deadflowr on 2018-02-04
Your Ambiance theme is broken.
A) try reinstalling the theme package (should be light-themes)
B) see if it's beyond just the ambiance theme and switch over to radiance for a moment to compare.

You can try a purge and reinstall, (you would also need to reinstall the ubuntu-desktop and ubuntu-artwork packages as those will get purged along with the theme package)

Or just try a quick install --reinstall command like so
```
sudo apt install --reinstall light-themes
```


To switch themes quickly, open Appearance and select the theme from the theme dropdown (it only lists a few, ambiance and radiance being two of them)

---

### Post by f(fanta) on 2018-02-04
Switching to radiance didn't resolve the issue. I also tried purging and reinstalling light-themes, along with ubuntu-desktop and unity, and rebooting, but it didn't solve the issue.

---

### Post by mc4man on 2018-02-04
What do these return
```

apt-cache policy gnome-session unity-control-center libgtk-3.0
```
```
env | grep  -E 'DESKTOP_SESSION|JOB'
```
```
 cat /etc/X11/default-display-manager
```

---

### Post by TheFu on 2018-02-05
> **f(fanta) said:**
> The new user has the same issue.

Now we know for certain that it isn't a userid config issue. That is something.
It is a system-wide issue.

---

### Post by f(fanta) on 2018-02-05
> **mc4man said:**
> What do these return [...]


Thanks. I ended up re-installing Ubuntu.

---

