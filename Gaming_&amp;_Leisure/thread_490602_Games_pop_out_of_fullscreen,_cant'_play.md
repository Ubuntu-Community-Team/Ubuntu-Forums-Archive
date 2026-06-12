---
title: "Games pop out of fullscreen, cant' play"
date: 2007-07-02
forum: Gaming &amp; Leisure
---

### Post by InlawBiker on 2007-07-02
Hi all,

I'm running Fiesty, also using Beryl.  I stop Beryl before launching games to see if that solves it, but no go, it still happens.

Playing either UrbanTerror or even Neverputt, the game will suddenly pop out of fullscreen mode and go into window mode.  In the case of UrbanTerror I lose all control of the game - no mouse, keyboard input accepted.  I have to open a tty and kill the process to continue. 

Any pointers?

---

### Post by hikaricore on 2007-07-02
Run the game from a terminal instead of a launcher icon, and paste any error output you may get at the time of the window mode issue here.
Though my guess is that something else is grabbing focus and causing the resolution change.

---

### Post by FoolsGold_MKII on 2007-07-02
I've had the same issue before. Turns out Pidgim (previously GAIM) had received a message and was trying to notify me.

---

### Post by InlawBiker on 2007-07-03
> **FoolsGold_MKII said:**
> I've had the same issue before. Turns out Pidgim (previously GAIM) had received a message and was trying to notify me.

I think you found it!  I didn't notice Pidgin trying to tell me anything but I do have it running.  Thanks for the tip.

Greg

---

### Post by syväpaahto on 2007-07-03
It seems that Beryl and games(cedega/native) don't mix well. My games work perfectly well, but when I exit the games my entire system freezes. Shutting down beryl before starting games solves the issue.

---

### Post by InlawBiker on 2007-07-03
Correction to my last post - it's beryl causing the problem.  If I select Metacity as the window manager the problem goes away.

Since Beryl is pre-release software this isn't a Gnome issue, I'll submit this to the Beryl guys.

---

### Post by graigsmith on 2007-07-03
it could be related to your screensaver?

---

### Post by InlawBiker on 2007-07-05
Follow-up to your question - no, it's not a screen saver - I don't use one.

Greg

---

