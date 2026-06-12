---
title: "Boot difficulties (HELP!)"
date: 2009-04-09
forum: General Help
---

### Post by 00Davo on 2009-04-09
Okay, I'm running Ubuntu Intrepid Ibex (8.10), with GNOME and Compiz.

Recently, I stupidly managed to hose my dpkg "installed packages" list. I fortunately managed to get apt working again - there was a dependency cycle issue regarding libc6, which I managed to fix. apt seems to be working pretty much fine now.

However, my PC is not. It seems to boot pretty much normally, with the main loading bar - it does switch to the terminal boot-view for some reason at about 9/10ths of the boot. I reach the login screen safely, and login.

At this point, I get the usual black screen (with the mouse cursor in the middle). Normally, this screen appears for only a few seconds. However, it currently just sits on this screen, rather than loading my desktop. Worryingly, one of my hard drives makes odd noises during this stage - it spins down, then up again repeatedly during the boot. A S.M.A.R.T check with smartmontools says all my drives have "PASSED".

Given a few system reboots and X restarts (Ctrl-Alt-Backspace), I can eventually get past the black screen and into my system. But this issue is very worrying.

(Also, upon my booting up again to post this, my colour scheme has changed from the default orangy "Human", to something blue. I don't seem to be able to change it back. Is this a related issue?)

---

### Post by 00Davo on 2009-04-12
Ka-bump.

The original Human theme has now returned. Still getting disk-spin sounds and such, however.

---

