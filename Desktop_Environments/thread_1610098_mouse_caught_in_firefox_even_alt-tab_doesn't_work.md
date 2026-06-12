---
title: "mouse caught in firefox even alt-tab doesn't work"
date: 2010-10-31
forum: Desktop Environments
---

### Post by quindonl on 2010-10-31
Hello.

I'm having a VERY irritating problem.
When I start firefox the mouse seems captured by it.
I can use the mouse inside the firefox screen (change tabs, use menu, select/paste) but not anywhere else. Even if a popup appears (site wants to register a cookie) then I can only use the keyboard to "ok" it. 
alt-tab to another window is not possible.
Using the mouse in the gome-panel won't work.
I can get the mouse pointer anywhere on the screen but mouse clicks don't seem to register. I've had this problem before on 10.04 and the only thing that worked then was to create a new useraccount (a lot of hassle).

edit: The window manager also won't react to the mouse so closing the firefox window is not possible using the windowmanager buttons (X - 0)
It's also not limited to Firefox, after I closed firefox via it's menu and then started a gnome-terminal the mouse was caught in that. After closing the gnome-terminal and restarting firefox it degraded even further in that the mouse would'nt even work in the window itself anymore. Only a reboor would reset the problem. It seems to be userbased since my wife's account does not have this problem.

Anyone any idea's about what could cause this?

---

### Post by Skaperen on 2010-10-31
If this problem does not happen when first using a userid, but eventually later does happen, but yet another new userid created next it won't happen on, but especially if later it does happen on the 2nd user, it would seem some persistent Gnome setting might be at fault.  I do know some programs do capture the mouse for a reason.  One I know of them is QEMU.  But I would think that as soon as said program exits the effect would be gone.  OTOH, maybe the effect has to be turned off by that program (which it would not be doing if it crashes, or gets killed) AND it is stored persistently somewhere in Gnome.  I see no reason for a captured mouse or captured keyboard focus to persist after process exit, but maybe that is happening somehow.

I'd try "blowing away" (just move them into a backup directory) all the Gnome config files.  When the graphical login prompt is up, Ctrl+Alt+F1 to switch to the text mode, login there, make a temporary save directory, and move the Gnome stuff into there.  Logout and do Ctrl+Alt+F7 (or F8 or F9 or wherever X picked a virtual terminal to run on) to get back to X.  With the Gnome config files gone, Gnome just re-initializes with all new default settings.  It's like creating a new userid, but is really the same old one.  If the problem goes away, Gnome was the culprit.  If it persists, it's something else.  More experimenting may be needed to pin down the exact cause.

---

### Post by quindonl on 2010-10-31
Thank you for the suggestion. I will try it out.

---

### Post by quindonl on 2010-10-31
Before I tried the moving of the gnome settings on a hunch I disabled all visual effects. It worked. No more problems with the mouse capture (so far).

Seems like compiz is the problem.

---

### Post by salterlee on 2011-05-18
Had a similar problem with Atl-Tab. I went into Compiz Config Settings (System > Preferences), then "Window Management", then checked "Application Switcher" and it started working again. Hope you've got it sorted, but for anyone else who gets the problem, it's a good one to try.

---

