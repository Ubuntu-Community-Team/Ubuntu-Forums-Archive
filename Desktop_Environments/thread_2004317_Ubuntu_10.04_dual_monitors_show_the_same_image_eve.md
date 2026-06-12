---
title: "Ubuntu 10.04 dual monitors show the same image even when the box is unchecked"
date: 2012-06-15
forum: Desktop Environments
---

### Post by Father Time89 on 2012-06-15
I got ubuntu 10.04.4 and I'm trying to set up dual monitors

In the monitor preferences its got the pink and yellow screens next to each other and when I turn one off the corresponding monitor turns off, but the both show the same image all the time. Even though I have 'same image in all monitors' turned off.
I tried looking up my video card and I got this

lspci|grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)

So anyone know how to get it so they stop showing the same thing?

---

### Post by Father Time89 on 2012-06-15
Ok I followed the instructions on this link

[http://www.h3manth.com/content/fixed-enabling-desktop-effects-ati-ubuntu-lucid](http://www.h3manth.com/content/fixed-enabling-desktop-effects-ati-ubuntu-lucid)

2 3 and 5 didn't work but I did the others, and now the monitors are stuck on mirror screens. When I tell it to change it says

""Monitor Resolution Settings has detected that the virtual resolution  must be set in your configuration file in order to apply your settings.

Would you like Screen Resolution to set the virtual resolution for you? (Recommended)"

It asked for an admin password and when I give it one the window freezes, does nothing and I have to do a force quit. I try it again and same thing.

EDIT: I was made an admin and rebooted and now dual monitors work just fine.

---

