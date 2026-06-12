---
title: "[SOLVED] KDE 4.2 Disable Lock Session"
date: 2008-12-26
forum: Desktop Environments
---

### Post by sirdilznik on 2008-12-26
So I recently upgraded from KDE 4.1.3 to KDE 4.2 (yeah I know it's still Beta).  I'm really liking it a lot so far.  One little annoyance though.  Ever since the upgrade, if I leave my machine idle for a while when I come back the session is locked and I have to enter my password to get back to the desktop.  I never enabled anything to the best of my knowledge to have the session automatically lock after a while, it just sort of started happening when I upgraded to 4.2.  It works fine entering my password, but I don't want my session locking at all.  I've been searching through the settings and for the life of me can't find the right dialog to disable this.  I figured it would be something to do with the login manager (kdm).  Google searches have come up fruitless too.  Can someone point me in the right direction to disable automatic session locking?

---

### Post by txcrackers on 2008-12-27
It's in the screensaver settings.

---

### Post by sirdilznik on 2008-12-27
> **txcrackers said:**
> It's in the screensaver settings.

Thanks for the reply but no (at least in my case).  I never even had screensaver enabled.  I "fixed" the problem with a simple ```
killall -9 krunner
```Of course there may be side effects from that (though none that I've seen yet) and I'd have to kill krunner again after a reboot.  Not to mention there must be a cleaner way to do this.

Edit:  OK I found the proper way to fix this.  The setting is found under System Settings > Advanced > Power Management

---

### Post by bkorb on 2010-11-30
> **sirdilznik said:**
> 
Edit:  OK I found the proper way to fix this.  The setting is found under System Settings > Advanced > Power Management

> -> settings and profile -> lock screen on resume

There must be a new secret sauce.  It is unchecked for me and still insisting that I type in my password if I leave the keyboard untouched for a few minutes.

---

