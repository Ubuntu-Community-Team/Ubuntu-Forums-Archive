---
title: "Gnome Root Terminal Unwanted Autostart"
date: 2005-09-20
forum: Desktop Environments
---

### Post by wacole on 2005-09-20
I clearly caused this but I don't know how.   The Gnome Root Terminal autostarts whenever I logon in user (not root) mode (I receive an error message because it can't find a root password and then displays the terminal in non-root mode.)

How do I turn this off, please?

PS I tried Systems|Preferences|Sessions, clicked on the "Current Session" tab, clicked on the "gnome-terminal" line, clicked on "Remove", clicked on "Apply" and then Logged Out and Restarted.  Dang thing is still there.

Thanks very much for any clues that are offered.

Bill Cole

---

### Post by Xiata on 2005-09-21
[QUOTE=wacole]I clearly caused this but I don't know how.   The Gnome Root Terminal autostarts whenever I logon in user (not root) mode (I receive an error message because it can't find a root password and then displays the terminal in non-root mode.)

How do I turn this off, please?

PS I tried Systems|Preferences|Sessions, clicked on the "Current Session" tab, clicked on the "gnome-terminal" line, clicked on "Remove", clicked on "Apply" and then Logged Out and Restarted.  Dang thing is still there.

Thanks very much for any clues that are offered.

Bill Cole[/QUOTE]
 Do that while it is still running. Gnome doesn't seem to delete autostarts. If it doesnt go away, change its status icon thing to a trash can and then logout/logon. That should get rid of it.

---

### Post by wacole on 2005-09-22
Thanks very much for the suggestions.  I tried both techiques and was unsuccessful.  I may have misinterpreted your instructions, so here's the detail just in case.  

Here's what I did:

While the Gnome Root Terminal (GRT) screen was open I did System|Preferences|Sessions, clicked on the Current Sessions tab, clicked on Gnome Terminal, clicked on Style and selected "Trash" from the drop down menu.  Clicked on Apply.  Then Close.  Then logged out and logged back in.  GRT is still there - persistent little guy.

I also did - while the GRT was still active - System|Preferences|Sessions, clicked on Current Sessions tab, clicked on Gnome Terminal, clicked on Remove, clicked on Apply and Closed.  Then logged out and logged in again.  Still there.

Obviously I can live with this, but it sure would be nice if this part of Gnome behaved like nicely.  It also makes me wonder what I did in the first instance to have caused this.

Thanks much,

Bill Cole

---

### Post by Wolki on 2005-09-22
It#s not in the additional start programs in the session tab, is it?

OK, gnome program management is a big big mess. If you have a program that always autostarts, try this: Set "Save changes to session" in the session preferences. Then, close all open programs and log out. Gnome will now save which windows are open - in this case, none. After logging in again, disable "Save changes to session" again. It should be away now.

---

### Post by wacole on 2005-09-23
Thanks very much.  It worked as you described - go figure.  Really appreciate the help.  I hope the Gnome folks sort this weirdness out soon.

---

### Post by Dooglus on 2005-09-23
All you need to do is log in, close down the things you don't want running, then click system -> log out, make sure "save current setup" is checked, and then log out.

When you log back in, you won't see the rogue terminal.

---

