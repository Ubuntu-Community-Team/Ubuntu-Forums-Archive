---
title: "Screen resolution lost"
date: 2008-02-20
forum: Desktop Environments
---

### Post by kristjans on 2008-02-20
I started Urban Terror and figured I had no sound. I restarted the game, and Urban Terror now displayed a black screen. Then I figured out the problem I had with the sound - my monitor speakers we're plugged in, instead of headphones from last night. Ctrl+Alt+Deleted out of my frozen system and logged in. I lost my screen resolution! Tried it a couple of times again, until I noticed that:

[color=red]edit: I don't have that message any more[/color]
> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-vgPtlXXifL: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in.

My [xorg.conf](http://pastebin.com/m58f4bb96) shouldn't have any problems, video card (7600 GT) drivers should be installed... I can't figure out what happened.

EDIT: One more CTRL+ALT+DELETE and no error messages now. Also, Gnome is fully themed again. Still, low resolution!

EDIT2: Restart > Log in > No picture.
Ctrl+Alt+F1 to terminal, back to GUI with Ctrl+Alt+F7
Screen is white, GUI buttons are working, Compiz is working.

---

