---
title: "Login manager"
date: 2005-06-03
forum: Desktop Environments
---

### Post by Peter Alien on 2005-06-03
Can anyone tell me what is the Login Manager for ?

I have Ubuntu 5.04 and i instaleed KDE 3.4 later, and i make several changes in Login Manager, mas when i reboot, the login stays the same. It keep asking me for the user and password.

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=Peter Alien]Can anyone tell me what is the Login Manager for ?

 It keep asking me for the user and password.[/QUOTE]
Yes, this is exactly what it is supposed to do. This is what it is for. Does it answer your question?

Or did you try to reconfigure it so that it would not ask for password? What exact tool did you use to do it?

---

### Post by Peter Alien on 2005-06-03
For what i understood there are options in LoginManager (e.g. in tab "appearance" and "users") that permit me to modify the Login, for e.g. changing the login background or instead of writing the user and password, it appears a tab with the user that can login. Is this correct ?

If it is, the problem is that i changed a lot of things in Login Manager but the login stays always the same.


I used "K Menu" -> Preferences -> System Administration -> Login Manager (in KDE 3.4).

---

### Post by psychicdragon on 2005-06-03
[QUOTE=Peter Alien]I used "K Menu" -> Preferences -> System Administration -> Login Manager (in KDE 3.4).[/QUOTE]
I don't have kde installed, but...
It seems to me that this would modify kdm, which is not being used (gdm is the default display manager).

trying running this in a terminal:
sudo gdmsetup

---

### Post by Peter Alien on 2005-06-03
Yes, that's what i was looking for :)

I think KDE just "overwrited" GDM jog ;)

Many thanks psychicdragon  :grin:

---

