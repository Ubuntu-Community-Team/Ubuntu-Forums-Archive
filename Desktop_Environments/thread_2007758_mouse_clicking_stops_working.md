---
title: "mouse clicking stops working"
date: 2012-06-21
forum: Desktop Environments
---

### Post by robertbub on 2012-06-21
Sporadically, randomly, occasionally, clicking on my desktop (Gnome 2) stops working.  (I'm on 10.04.)  This only seems to happen when using VNC (remmina is the client, vino-server is the server).  I cannot find the pattern, but it's possible that I do a right-click.  In any case, in my most recent problem, the mouse cursor became a "hand", as if I'm trying to grab something.

ALT-Tab also stops functioning, making it difficult to switch to a different window.

Since I was unable to click to my other windows, ALT-F2 allowed me to bring a dialog to run something.  I brought up xterm (so obviously, typing into the keyboard works, and is thus not completely frozen).

I read somewhere that killing nautilus might help.  It didn't.

I also tried "compiz --replace".  Again, it didn't help.

When I got to the physical machine, I did a ALT-CTL-F1, and then switched back.  It didn't help.

The only thing that does work is to kill gnome-session (essentially, logging out of that X-Windows screen) and then logging in again.

Unfortunately, killing the gnome-session makes it difficult to use VNC and login.

Has anyone else experienced this problem?  Is there anything short of killing gnome-session that might fix it?

---

### Post by ajgreeny on 2012-06-21
> **robertbub said:**
> 
I also tried "compiz --replace".  Again, it didn't help.
What about **metacity --replace** instead in the Alt+F2 command box.  If it is compiz that is causing the problem your **compiz --replace** will not help, as that just makes compiz the window manager, so no change.  My command will make metacity the window manager instead.

---

### Post by robertbub on 2012-06-21
> **ajgreeny said:**
> What about **metacity --replace** instead in the Alt+F2 command box.  If it is compiz that is causing the problem your **compiz --replace** will not help, as that just makes compiz the window manager, so no change.  My command will make metacity the window manager instead.There is no existing **metacity** process running -- I only saw a **compiz** process running, and thus did the **compiz --replace**.  Does it matter what processes are running?

---

### Post by ajgreeny on 2012-06-21
> **robertbub said:**
> There is no existing **metacity** process running -- I only saw a **compiz** process running, and thus did the **compiz --replace**.  Does it matter what processes are running?
That was exactly my point.

If you are running 10.04 with compiz as the window manager, perhaps with the desktop cube etc, or at least some of the desktop effects from **System -Preferences -Appearance - Visual Effects** tab, then your command will do nothing.  Mine will change the window manager from compiz to metacity, which may solve your problem.

Give it a try next time it happens; you can get back to compiz if you want to with the command you tried first, "compiz --replace"

---

### Post by robertbub on 2012-07-03
> **ajgreeny said:**
> Give it a try next time it happens; you can get back to compiz if you want to with the command you tried first, "compiz --replace"This is didn't work.

However, after trying various **metacity --replace** and **compiz --replace**, I killed **firefox**.  That seemed to free up the mouse.

If it happens again, I'll try killing firefox first to see if that's the entire problem.

---

