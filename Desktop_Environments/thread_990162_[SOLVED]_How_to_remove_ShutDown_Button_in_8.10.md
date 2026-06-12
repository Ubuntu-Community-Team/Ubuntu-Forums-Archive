---
title: "[SOLVED] How to remove ShutDown Button in 8.10"
date: 2008-11-22
forum: Desktop Environments
---

### Post by godor on 2008-11-22
Hi,
how do i remove all shutdown buttons for a specific user under gnome? Editing gdm.conf seems not to work in 8.10.
I like to use Ubuntu in an public Terminal which the Logged in User should not Shut Down or Restart. Best would be to disable it also in the Terminal.
Thanks,
Guido

---

### Post by Izek on 2008-11-22
[Google Search](http://www.google.com/search?hl=en&q=disable+shutdown+ubuntu&btnG=Google+Search&aq=f&oq=)

aaand I didn't find anything for disabling shutdown from the terminal.

---

### Post by aysiu on 2008-11-22
I would look into Gnome Pessulus:
[http://www.linux.com/feature/62060](http://www.linux.com/feature/62060)

Unless you remove all Gnome applets, removing the shutdown applet will still allow the user to add the applet back in. But then you won't have any of the other applets either.

And, by default, unless the user is in the *admin* group and knows the user password, that user cannot shut down from the terminal.

---

### Post by godor on 2008-11-23
Thank you, Pessulus is helping me a lot.
But I want to allow the user to logout, is it also possible to remove only the Shut Down option from the System menue?

---

### Post by godor on 2008-12-05
my solution was the Authorisations Tool in the Administartion Section, here I just asked for the admin password, when power of.

---

