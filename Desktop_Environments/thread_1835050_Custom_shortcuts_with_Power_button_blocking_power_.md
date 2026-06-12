---
title: "Custom shortcuts with Power button blocking power management setting"
date: 2011-08-28
forum: Desktop Environments
---

### Post by Waldeinburg on 2011-08-28
I run Ubuntu 11.04 on a MacBook 1,1. I like Shift+Power button (XF86PowerOff) to suspend my laptop while Power button alone should make Gnome ask me what to do. In *Power Management* I set the Power key behavior to "Ask me". If make a custom shortcut in *Keyboard Shortcuts* everything seems OK, but after a restart the Power key does nothing while the Shift+XF86PowerOff shortcut works. What's happening?

(In case it helps anyone who wants the same or somebody has a better way to do it: I put "myusername ALL = NOPASSWD: /usr/sbin/pm-suspend" at the end of /etc/sudoers and use "sudo pm-suspend" as the command for the shortcut.)

---

### Post by Waldeinburg on 2011-08-30
Mmh, no replies. Any ideas for a workaround then? Is there an easy way to trigger a shutdown/restart dialog from the command line which could be triggered by a shortcut?

---

### Post by Krytarik on 2011-08-30
Yeah, no idea why the default Power key behaviour stops working after setting up the custom shortcut. But this would be the workaround:
```
gnome-session-save --shutdown-dialog
```
[http://manpages.ubuntu.com/manpages/natty/en/man1/gnome-session-save.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/gnome-session-save.1.html)

Greetings.

---

### Post by Waldeinburg on 2011-08-31
Ah yes, exactly the workaround I was looking for! Thanks!

---

