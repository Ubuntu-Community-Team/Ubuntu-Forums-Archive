---
title: "GNOME/Nautilus boot problem."
date: 2006-08-17
forum: Desktop Environments
---

### Post by justsomemo on 2006-08-17
I am in love with Ubuntu and Gnome.  Just made the switch from XP about a month ago, and now I can't get myself to leave my laptop alone.

With that said, I have run into a problem that is becoming very annoying and beginning to kill my linux/ubuntu/gnome experience.

Sometimes when I login from the GDM screen, my desktop will load halfway, the splash dialog will get to about the Nautilus part, and all of a sudden the screen will go black or show a few blocks of gray on a black screen right before turning into the black screen command prompt for me to enter my login and password.  If I don't enter anything for a few seconds, my GDM screen loads again.  This is a random occurrence, but sometimes it happens up to 5-6 logins in a row.  One thing that is interesting is that if Firestarter gets a chance to start (as it is one of my startup applications) then the desktop and gnome loads fine.

I installed fluxbox just for kicks and to check it out.  This problem never occurs when I boot into fluxbox, so I am left to think it is a gnome/nautilus problem.  Any ideas?  I have tried creating different user accounts, but it happens on them also.  It doesn't occur while I login as Root though.

Thanks for any help.  These forums are responsible for my transition to linux and I would just like to thank all of you for helping me through with your posts.  ;)

---

### Post by crackseller on 2006-08-17
Sounds to me like a session problem. Check what apps are loaded with the session (it's either Settings > Session OR Administration > Session). Some apps cause that kind of behaviour if they're loaded before/after the gome desktop. I suggest you disable all unnessessary applications, then login, enable one app/logout/login/... etc. If you enable one app after another for your session you may find the reason of your problem this way.

---

### Post by justsomemo on 2006-08-17
Just got through trying that, but didn't help.  Disabled everything short of firestarter, gnome-power-manager, update-notifier, and volume manager.

Any other suggestions?  Just so it is known, I've tried completely uninstalling GNOME and reinstalling it.  Problem persists.

---

### Post by ozorba on 2006-08-17
Another option is to rename .gnome, .gnome2, .gtkrc-2.0 (i.e. Gnome related files/directories) in your home directory and re-run....

---

### Post by justsomemo on 2006-08-17
Rename them to anything you mean?

---

### Post by justsomemo on 2006-08-17
Well, tried that to no avail.

Since I wanted to play around with my partitions and haven't spent much time customizing yet, I decided to do a full format of my ubuntu partition and clean install.  I did, and the problem went away...that is for a while.  It started again once I installed fluxbox.  Since then, I have deleted fluxbox and all traces, but the problem still occurs.  The last time this started happening was right after I installed KDE on my ubuntu.  [I removed it within a few minutes [and not because of this problem either] :) )

If anyone has any suggestions, please let me know.

---

