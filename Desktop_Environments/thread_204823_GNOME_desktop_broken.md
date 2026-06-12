---
title: "GNOME desktop broken"
date: 2006-06-27
forum: Desktop Environments
---

### Post by meegosh on 2006-06-27
I recently switched from one monitor to two, which is working in X.

However, after I log in to a GNOME session with GDM I do not see the splash screen with icons for various processes. My hard disk churns and I have a feeling that the session is loading, but it is just not displayed.

GNOME Failsafe also does not work, but KDE does work correctly, splash screen and all.

I am pretty sure that the handoff between GDM and the Gnome Desktop is where things get lost, because KDE is able to work correctly with GDM as my Desktop Manager.

Any ideas where to look? I have a feeling that I just need to whack a configuration setting somewhere...

-- Stuck in KDE

---

### Post by bjourne on 2006-06-27
Try whacking (rm -rf) ~/.metacity. Yes it is probably a settings problem and one of the ~/.*-directories is to blame.

---

### Post by meegosh on 2006-06-27
Whacking that directory doesn't fix it.

I also tried using KDM as the display manager. No dice. GNOME session still fails, KDE session still works.

I also tried making a new user, and when that user logs in GNOME does work! However, if I replace my home directory with an empty directory and try to login, GNOME still doesn't work.

Any further ideas? It seems like a setting is stored per user somewhere OUTSIDE the user's directory.

Making a new user for myself is not really an option. I also suspect that if I delete my user and make another one with the same login, that user won't be able to use GNOME either.

---

