---
title: "thunderbird doesn't restore emails"
date: 2009-01-09
forum: General Help
---

### Post by uwes on 2009-01-09
Yesterday, I shut down my computer and switched of the power before the shut down was complete. A whole lot of settings were lost by this, for example ff doesn't remember not to accept cookies, doesn't remember the home page, etc. This has occured for the second time, and I think about filing a bug report. However, I know too little about what actually broke to do so.

But now to the real problem. Thunderbird also forgot everything, my account, my emails, and all the settings. Yet, the .default-profile folder is still there and it also contains all my mails and all settings, thunderbird just doesn't find them. I also tried to start in the command line with the -P option, but there's nothing but the (empty) default profile to choose from.

I also tried to create a new profile xxx.default and then copy just the contents of the profile folder, but to no avail. I can copy my old "Local Folders" folder into the new profile and the mails are found (but only, if an account has been created before), but this doesn't work for my account  settings. Does anyone have an idea what to try to avoid having to do everything manually? Please let me know, if you need more info.

---

### Post by ajgreeny on 2009-01-09
> This has occured for the second time, and I think about filing a bug report. However, I know too little about what actually broke to do so.Whilst I do sympathise, I do not think this could be described as a bug; you said it yourself, you turned off the power before the shutdown had completed, which is probably worse than a power outage while you are working on something as a lot of files are possibly corrupted as they tried to writr to disk when you did the poweroff.

I think the best way forward is to completely rename your original *~/.mozilla-thunderbird* folder (I'm assuming you have it, of course) not just the *alphanumeric.default* file that holds your profile.  This will mean that thunderbird makes a new hidden folder together with a new *profiles.ini* file, which tells thunderbird which profile to use.  If this is what you have already tried, my apologies, and if that is the case, I think your mails may be corrupt and a backup copy (you have one, of course?) may be needed.

---

### Post by uwes on 2009-01-09
Btw, my gnome settings like single-mouse-click or nautilus appearance are also gone... Maybe, this helps locating the bug.

---

### Post by ajgreeny on 2009-01-09
Sounds as if all your settings were corrupted by the early switch-off.  Rename your ~/.gconf folder and then restart gnome by logging out and a new .gconf folder will be made and you can start again with all your settings for nautilus etc etc.  I think this may be a salutary lesson in not being too quick with the power switch.

---

### Post by uwes on 2009-01-09
I did try to also delete the profiles.ini, but that did not help either. I did not even think of the possibility that those files might be corrupted, but they probably are, at least this would explain why thunderbird doesn't read them. The mails in the local folders where not corrupted, but I had to redo the whole configuration manually, which took me quite a while.

Thanks for your assessment of the situation. I don't quite see your point why you don't consider it as a bug, though. Following your argumentation, shouldn't at most be the one file corrupted which was being written while the power was turned off? And since it has happened for the second time and the same applications are affected, shouldn't one expect those applications to handle the files more carefully?

edit1: I don't think there's a reason to rename the .gconf folder, since everything seems to be working fine. I guess, it has already been rewritten because of being unreadible. I have no problem going straight for reconfiguration.

edit2: I try to do my best to keep my hands off the power switch ;-)

---

