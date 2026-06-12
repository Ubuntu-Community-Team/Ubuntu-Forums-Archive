---
title: "Do Logs me out when I use New Wave theme!!!"
date: 2008-10-18
forum: Desktop Environments
---

### Post by Umang on 2008-10-18
Hi!
This is my craziest experience with GNOME and GNOME-Do. I installed the New Wave theme and logged out. Now every time I log in and press <Super> + <Space>, I get a hazy black screen. After around 5 seconds, I get the Login Window! It not only crashes itself, but also everything else that is open!

I tried switching back to some other theme and I get GNOME-Do working perfectly!

I'm running Ubuntu 8.04 Hardy, GNOME-Do 0.6.1.0, New Wave 0.6 (theme + GDM with list + Lock Dialog theme). No compiz, no emerald.

I get the following even on themes that GNOME-Do works on.
```

:~$ gnome-do

** (Do:12551): CRITICAL **: gnome_desktop_item_get_localestring: assertion `item != NULL' failed

** (Do:12551): CRITICAL **: gnome_desktop_item_get_localestring: assertion `item != NULL' failed

** (Do:12551): CRITICAL **: gnome_desktop_item_get_string: assertion `item != NULL' failed

** (Do:12551): CRITICAL **: gnome_desktop_item_get_string: assertion `item != NULL' failed

** (Do:12551): CRITICAL **: gnome_desktop_item_get_localestring: assertion `item != NULL' failed

** (Do:12551): CRITICAL **: gnome_desktop_item_get_localestring: assertion `item != NULL' failed

** (Do:12551): CRITICAL **: gnome_desktop_item_get_string: assertion `item != NULL' failed

** (Do:12551): CRITICAL **: gnome_desktop_item_get_string: assertion `item != NULL' failed
```

What should I do?

Umang

---

### Post by Umang on 2008-10-18
Downgrading to GNOME-Do 0.4 from the Ubuntu repository fixes this, but I don't like Do 0.4.

Any ideas?

Thanks a lot!

Umang

---

