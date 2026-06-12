---
title: "Power management"
date: 2009-02-18
forum: General Help
---

### Post by zy_guy on 2009-02-18
Just a question, don't know where else to post it. I was wondering why the power management utility placed in the preferences protion of the system menu rather than the admin portion? just wondering.

thanks
David

---

### Post by user-max on 2009-02-19
Maybe because the features that are offered by that tool are more of an individual user preference, such as screen brightness, rather than administrative options.

---

### Post by zy_guy on 2009-02-19
Not really. The control it ofers is how long to wait until shut down of the display or hard drive, and what to do with the power button when it is pushed (nothing, hybernate, turn off). These are admin option not user.

---

### Post by unutbu on 2009-02-19
System>Pref is for properties that are configurable on a per-user basis.
System>Admin is for properties that are configurable on a system-wide basis.

If you have more than one user, then each user can set their own System>Pref>Power Management properties.

---

### Post by sdennie on 2009-02-19
This is possible via PolicyKit/dbus.  Go to System->Administration->Authorizations and you'll see things for gnome-power-manager.  If you look at those settings, you'll see that people physically sitting in front of the machine are allowed some conveniences that are normally only allowed to root/admin.

---

### Post by user-max on 2009-02-19
In my power management options, I have screen brightness on login, what to do when laptop lid is closed, when to shutoff display when idle and so on... Maybe because im running ubuntu on a laptop.

---

