---
title: "This program cannot start until you start the dbus system service."
date: 2006-09-20
forum: Desktop Environments
---

### Post by bakert on 2006-09-20
I hope someone out there can help me.

I added ssh-agent and ssh-add to System, Preferences, Sessions, Startup Programs.  They didn't seem to work, so I removed them.  This may or may not be coincidental to my problem.

Now whenever I boot/login I get:

"This program cannot start until you start the dbus system service."

If I disable gnome-power-manager in the same place (System, Preferences, Sessions, Startup Programs) the message goes away, but I can no longer put my laptop to sleep with the keyboard shortcut and Suspend does not appear on the logout menu.

I've tried /etc/init.d/dbus restart.  I've tried rebooting.  I've tried logging in to failsafe Gnome, restarting dbus and then coming back in to a normal Gnome session.  No dice.

Strangely, I can run KDE, then run gnome-power-manager and then I am able to put the machine to sleep and wake it up (with the keyboard).

I'd really appreciate any ideas you have as to what I can do to get Suspend back into Gnome.

Thanks, Tom

---

