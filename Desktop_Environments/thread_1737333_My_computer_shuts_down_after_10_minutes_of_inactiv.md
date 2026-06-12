---
title: "My computer shuts down after 10 minutes of inactivity"
date: 2011-04-23
forum: Desktop Environments
---

### Post by adit on 2011-04-23
My computer shuts down after 10 minutes of inactivity.  In power management preferences, I have selected:
Put the computer to sleep when inactive for 0.10
I expect the computer to sleep after 10 minutes.  But it shuts down.

---

### Post by Paddy Landau on 2011-04-23
You don't say what version of Ubuntu you have. Or are you using Wubi?

Some systems have hardware incompatible with Ubuntu. In those cases, it tries to go to sleep, but the incompatibility means that instead it shuts down.

Wubi has its own problems and can be highly temperamental with sleep (and hibernate won't work).

---

### Post by adit on 2011-04-25
I have ubuntu 10.10.  I don't use wubi.  I am able to put the computer to sleep manually.  I think there is problem with my power management settings.

---

### Post by Paddy Landau on 2011-04-25
> **adit said:**
>  I am able to put the computer to sleep manually.  I think there is problem with my power management settings.
Hmm, that makes it a bit confusing. You put it to sleep manually, and it wakes up OK; but when it goes to sleep automatically, it actually shuts down.

Question: Is this a laptop that sometimes runs on a battery? If so, when you look at your Power Management, check both *On AC Power* and *On Battery Power*.

If they are both OK, try disabling your screensaver. System > Preferences > Screensaver > uncheck *Activate your screen saver when computer is idle*.

Let us know what happens.

---

### Post by adit on 2011-04-25
I have Dell Inspiron  1525 laptop.  If left alone:
1) It shuts down after 10 minutes on battery power
2) It sleeps after 30 minutes on AC power

In Power Management Preferences window I have the following settings:
On AC power tab:
Put the computer to sleep when inactive for 0.10
On Battery power tab:
Put the computer to sleep when inactive for 0.10

In Screensaver Preferences window there is a checkbox.
Activate screensaver when computer is idle
That is already unchecked.

The configuration files and log files in my system will give more information.  I don't know which files to post.

---

### Post by Paddy Landau on 2011-04-26
Do you close your laptop lid when leaving the computer? If you do, what setting do you have for "When laptop lid is closed" for both AC and battery?

If this isn't the problem, then I'm sorry, I don't know where to go from here. Let's hope someone else with more knowledge can help.

---

### Post by adit on 2011-04-26
These problems occur even when laptop lid is open.
These problem started since I played with keys in gconf-editor.
I think I should reinstall the entire operating system.

---

### Post by Paddy Landau on 2011-04-26
> **adit said:**
> I think I should reinstall the entire operating system.
That might help; but then again, it might not. Boot from a Live CD, set the power management settings the same, and see what happens with the Live CD. If it works, at least you know it's not a hardware issue.

---

### Post by Krytarik on 2011-04-26
> **adit said:**
> 
These problem started since I played with keys in gconf-editor.

You don't happen to remember what keys you edited, right?
Or at least the rough direction?

---

### Post by Paddy Landau on 2011-04-26
> **adit said:**
> These problem started since I played with keys in gconf-editor.
I missed that, silly me.

In gconf-editor: apps > gnome-power-manager.
Have a look around and see what you might have changed.

---

