---
title: "Remove &quot;Set up Mail...&quot; option from notifier"
date: 2010-05-26
forum: Desktop Environments
---

### Post by yippy on 2010-05-26
I've configured Gmail as my default mail client, and installed gm-notify to enable it on the notifier icon dropdown, but I still have the "Set up Mail..." option to configure Evolution.

Any idea how to get rid of the "Set up Mail" option?

---

### Post by yippy on 2010-05-27
Now I've also installed Pidgin instead of Empathy, and have the same issue there.  I have both the Pidgin option and the old Chat option.

There has to be a way to edit the notifier list.

---

### Post by yippy on 2010-05-28
Finally just uninstalled Evolution and Empathy, and that did the trick.  I had to reboot though, just killing the gnome bar didn't update it for some reason.

---

### Post by BigSnacks on 2010-05-28
Is it possible to uninstall these in my daughter's profile, but leave them in mine, or will removing them apply to all users?

---

### Post by BigSnacks on 2010-05-28
Tested it for myself and... it applies to all users.  D'oh!

---

### Post by x-shaney-x on 2010-05-28
As far as evolution is concerned you could go to "Edit > Plugins" on your daughter's evolution and disable the indicator plugin.
I don't think there is any way to remove empathy from indicator per user other than to remove the indicator applet from the panel.

---

### Post by Dr.Snuggles on 2011-08-04
Reviving this thread because it was the first result I found on Google, and it doesn't really give any answers:

All you have to do is
```
sudo apt-get remove evolution-indicator
```log out, log back in and the annoying "Set up Mail..." should be gone.

---

