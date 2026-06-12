---
title: "GDM fails Gnome login, xfce and kde OK."
date: 2007-11-26
forum: Desktop Environments
---

### Post by rosslaird on 2007-11-26
This is odd: after a recent reboot (I have a laptop), gdm fails to complete a gnome login. I have tried various things, most of which were the result of switching to a console and seeing what was running. Both tracker and beagle were running (that doesn't sound right...), but after stopping both I still have the problem. It seems also to be window-related. What I get after login is the tan screen and a mouse. If I hit f12 I get the beagle search window with no border. Alt f2 doesn't work, so I can't try to start metacity that way. I know there is some voodoo to start it from the console session, but I forget exactly how to do that. Something about export 0:0 or similar.

Anyway, it's not just the window borders. Essentially I'm getting a blank screen with no warnings or errors and no functionality.

Suggestions are welcome. I have an important presentation tomorrow, to about 150 people, and I'd rather that my computer was working properly...

Ross

---

### Post by neilengineer on 2007-11-27
What did the error say?
What did you do before this problem appear?
Seems some service is not started?

I had met lots of GDM problems, almost every time I resolved it by reinstalling it.   So, you may try to reinstall gdm and see.

---

### Post by rosslaird on 2007-11-27
> **neilengineer said:**
> What did the error say?
What did you do before this problem appear?
Seems some service is not started?

I had met lots of GDM problems, almost every time I resolved it by reinstalling it.   So, you may try to reinstall gdm and see.

There are no error messages. X starts. It just starts into the gnome splash screen without the little panel showing things starting up. 

I didn't do anything (e.g. installing new software, changing settings, etc.). It's just one of those things that just happened...

It's not a gdm problem. Same thing happens with kdm. Besides, xfce and kde (and openbox, and fluxbox, and blackbox) all work fine from gdm. So definitely it's gnome itself.

I have managed to get into gnome using openbox as the window manager, so I think in fact it's a metacity problem. 

R.

---

