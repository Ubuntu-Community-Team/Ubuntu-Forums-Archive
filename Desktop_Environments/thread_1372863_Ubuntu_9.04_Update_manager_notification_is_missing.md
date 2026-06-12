---
title: "Ubuntu 9.04 Update manager notification is missing!?!?"
date: 2010-01-05
forum: Desktop Environments
---

### Post by highland_dreamweaver on 2010-01-05
Hi all,
Lately I've noticed that the update manager notification doesn't work either. Together with minimisation problems and the sound problems I am beginning to regret updating in the first place. Twice now I have randomly activated the update manager to find loads of new packages but I never seem to get any warning that they are there! This version is seriously messing with my state of remaining cool!:confused:

Anyone got any ideas what went wrong?

Steve...

---

### Post by SteveDee on 2010-01-05
I can only suggest you open Update Manager and check the settings via the Settings button.
In the Updates tab, ensure that "Check for updates" is ticked and initially set period to "Daily"

---

### Post by highland_dreamweaver on 2010-01-06
Hi Steve,
Thanks for the reply! Sadly it doesn't help... I've had those settings all along and it still doesn't work! The only thing I can think of was that during the upgrade to the new version the bug report manager I have enabled was seriously tested out. There were dozens of bugs detected in various files some fixed and some pending! I can only guess that together some of them are causing havoc! I guess I can only wait till they are all fixed or I get fed up and do a retrograde install of Hardy or Intrepid where I know everything was working!

Thanks anyhow Steve! I appreciate it!

Steve...

---

### Post by SteveDee on 2010-01-06
My only other suggestion is to open a terminal and type:-
sudo gconf-editor

In the "apps" branch take a look at "update-notifier" and "update-manager" settings.

---

### Post by highland_dreamweaver on 2010-01-16
Hi Steve,

Sorry for the delay responding! No need now! Between this and the other problems I had I finally blew my cool and reverted to Intrepid... hence the delay responding. All is rosy now, but I think I shall wait to see how lucid is before I try upgrading again. Just too many bugs to handle at one time... just couldn't handle it!

Steve...

---

### Post by mister_playboy on 2010-02-01
Enter this in the terminal to get the 8.10 notification behavior in 9.04:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

---

