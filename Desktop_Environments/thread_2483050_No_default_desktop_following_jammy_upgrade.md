---
title: "No default desktop following jammy upgrade"
date: 2023-01-19
forum: Desktop Environments
---

### Post by takeawaydave on 2023-01-19
I have performed a number of upgrades since v 16.04 and now running 22.04

In the mean time I installed mate desktop which has now been deinstalled since I love the new 22.04 look.

Comparing my desktop to a freshly installed 22.04 machine it looks different through. 

For example the menu bar and the top bar.

Following a "dconf reset -f \" the desktop appears as shown with no buttons on top bar etc.

How can I get this to default jammy ? I suspect default settings are still from an older version.

None of the Appearance settings change the desktop either.[IMG]https://snipboard.io/jkouQy.jpg[/IMG]

---

### Post by ActionParsnip on 2023-01-19
If you create a new user and log in as that, is it all OK as the fresh user?

---

### Post by takeawaydave on 2023-01-19
I tried a simple:

sudo useradd -d /home/test_user test_user

and then set a password and tried to login however I was returned after a few seconds to the log in screen.

If I try to unlock the Settings context menu to add a user via the graphical approach its grey out

 [IMG]https://snipboard.io/TeC4dn.jpg[/IMG]

---

