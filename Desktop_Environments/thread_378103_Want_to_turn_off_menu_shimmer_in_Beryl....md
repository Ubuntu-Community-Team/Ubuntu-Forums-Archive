---
title: "Want to turn off menu shimmer in Beryl..."
date: 2007-03-06
forum: Desktop Environments
---

### Post by konungursvia on 2007-03-06
The menus are now shimmering and wavy which takes too long. I love beryl but this part I wish I could turn off. Can this be done?

---

### Post by maniacmusician on 2007-03-06
Of ocurse. There are options for everything in Beryl.

Right click on the Beryl Icon > Bery Settings Manager > Visual Effects > Animations 

You want "Create #2" and "Close #2"

edit: in that same dialog, you can  also edit stuff like the speed of the animation,  what types of objects it affects, etc. 

Enjoy.

---

### Post by konungursvia on 2007-03-06
Thanks very much! the only ohter question is, how do I make beryl start itself when I log in? :)

---

### Post by medley on 2007-03-06
> **konungursvia said:**
> Thanks very much! the only ohter question is, how do I make beryl start itself when I log in? :)

One thing you can do is go to 'system settings' and select the 'advanced' tab. Under 'session manager' specify 'restore a manually saved session' hit apply and close 'system settings'. Now you should have an option to save your session under K menu. Make sure beryl is running, and everything else that is running (or not) that you want next time you log on. Click 'save session'. Next time you log on, beryl should be running.

Works for me at any rate.

---

### Post by konungursvia on 2007-03-06
Oh, I use gnome, and what you're saying sounds kde-ish. ;) But if it's that complex, I'll just run it from the command line once a day.

---

### Post by maniacmusician on 2007-03-06
nah don't sweat it, good sir. It's easy in both Gnome and KDE.

For KDE: 
> ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager

For Gnome:
> System > Preferences > Sessions > "Startup Programs" Tab
Click "Add"
Type in "beryl-manager"

I use beryl in both Gnome and KDE. I must say, I like that KDE has a command-line way of doing it...it's much quicker than doing it graphically. But,  it's still easy whichever way you do it.

Enjoy! :)

---

### Post by konungursvia on 2007-03-06
Aww you're the best, maniac. Done what you suggest! Thanks a fafillion/.

---

### Post by maniacmusician on 2007-03-06
No problem, everyone deserves a little Beryl fun.

---

