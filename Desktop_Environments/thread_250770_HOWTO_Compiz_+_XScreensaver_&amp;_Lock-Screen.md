---
title: "HOWTO: Compiz + XScreensaver &amp; Lock-Screen"
date: 2006-09-04
forum: Desktop Environments
---

### Post by stontyro on 2006-09-04
So, how many like to lock the screen when you walk away?

Here's how to make it work with compiz:

System->Preferences->Sessions:
Under Startup Programs tab:
    add "gnome-screensaver --display=:93".
Delete any other gnome-screensaver entries.

Next:
Run 'csm' the compiz settings manager.
Select General Options.
Under the Simple Strings tab:
    set command N to "gnome-screensaver-command --lock"
Under the Action Bindings tab:
    set command N 'key' to ctrl, alt, and "l" (lower case L).
N can be any of the commands/key bindings as long as they correspond.

Next:
I know you hate this... log out, log in.
Now try it out! (Ctrl+Alt+l should lock your screen)

---

