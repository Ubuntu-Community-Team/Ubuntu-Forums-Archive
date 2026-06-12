---
title: "[SOLVED] Delete all personal data"
date: 2008-12-08
forum: General Help
---

### Post by balta on 2008-12-08
Hi!
I've been trying to delete all my personal data regarding emesene, but even though I clicked on `forget me` and I used Synaptic to `completely remove` the program when I reinstall it, when I sign in, it still remembers my avatar, my personal message and my settings. I want to remove all of them!
I've already tried to check if during the uninstallation some files created during the installation were not removed, but even if I checked all of them it seem it removed everything correctly.
**So what files must I delete to delete all of my saved data of emesene?**

please help me!

ps: for more info have a look at: [http://ubuntuforums.org/newthread.php?do=newthread&f=331](http://ubuntuforums.org/newthread.php?do=newthread&f=331)

---

### Post by balta on 2008-12-10
> "rm -rf ~/.config/emesene1.0" 
deletes all emesene-user-related data

can anybody please mark this thread as solved? thanks

---

### Post by chronographer on 2008-12-10
your settings are stored in your home directory. So firefox saves all your history, bookmarks etc in /home/<username>/.mozilla/... and as the above poster states, emesene stores them under /home/<username>/.config/... It is a handy feature, as when / if you reinstall you can keep your home directory and everything will appear the same when you launch applications!

---

### Post by geirha on 2008-12-10
> **balta said:**
> can anybody please mark this thread as solved? thanks
The person who starts the thread can mark it as solved. Click Thread Tools.

---

