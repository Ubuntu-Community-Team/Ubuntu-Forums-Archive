---
title: "screen lock on resume based on HAL"
date: 2008-05-23
forum: Desktop Environments
---

### Post by wgandhi on 2008-05-23
Hi

I have suspend/resume working well on my intel core 2 duo system with a DQ965GF board running Hardy. I had to unload the uhci_hcd module to make everything work.

Only issue is that if I suspend the system using the keyboard (special key) or the gnome log out button, I am presented with a password protected screen saver on resume. This is annoying as I dont want to remember 1 more password for my home system

I used gconf-editor to disabled the lock on suspend. If I suspend using sudo pm-suspend on the command line, I dont get the resume screen password locked. My guess is that the gnome logout button and keyboard use some HAL command which in turn uses pm-suspend. However, HAL introduces the password locked screen... How do I disable it?

-Wishwesh

---

### Post by sdennie on 2008-05-23
What did you change in gconf-editor?  On two laptops I've gone to /apps/gnome-power-manager/lock and unchecked suspend and hibernate and it's worked fine (it's not the best idea to do this but, my parents very old and get confused when a password dialog appears).

---

### Post by wgandhi on 2008-05-23
Those are the exact options I unchecked. It did solve the issue of getting a password on resume if I use the pm-suspend command at the command prompt.
However the log off button and keyboard still get the paswword dialog box.

---

### Post by wgandhi on 2008-05-24
Ah.. Solved the issue. It appears that the password dialog shows up if the gnome screen saver is running. Weird... Seems like a bug.

---

### Post by nbd on 2009-03-10
Here is what gconf-editor long description says about /app/gnome-power-manager/lock/suspend:

"Whether the screen is locked when the computer wakes up from a suspend. Only used if lock_use_screensaver_settings is false."

So the use_screensaver_settings must be also unchecked.

---

