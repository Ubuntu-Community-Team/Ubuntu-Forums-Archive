---
title: "Stop once and for all asking user &quot;refresh system repositories&quot; &amp; notifications"
date: 2019-06-27
forum: Desktop Environments
---

### Post by jean.eastcode on 2019-06-27
I don't understand why any std no admin user should be notified about the need to refresh the system repositories ??

anyway, the damn thing can't stop asking for admin rights to any user opening a Gnome session.
Setting "automatically check for updates to Never" just doesn't seem to help.

please help!

---

### Post by CatKiller on 2019-06-27
> **jean.eastcode said:**
> I don't understand why any std no admin user should be notified about the need to refresh the system repositories ??

Because they need to check for updates. Especially those that have turned off automatic checking, like you. 

> anyway, the damn thing can't stop asking for admin rights to any user opening a Gnome session.
Setting "automatically check for updates to Never" just doesn't seem to help.
That setting is for people that want to check manually, not for people that don't want to check at all. All machines need to check for and install security updates, including yours.

---

### Post by mc4man on 2019-06-30
> **jean.eastcode said:**
> I don't understand why any std no admin user should be notified about the need to refresh the system repositories ??

anyway, the damn thing can't stop asking for admin rights to any user opening a Gnome session.
Setting "automatically check for updates to Never" just doesn't seem to help.

please help!

Not sure I've ever seen a notification to refresh the system repositories but anyway,
```
sudo apt-get purge update-notifier
```
If you (admin), want to handle updates yourself then also remove update-manager

---

