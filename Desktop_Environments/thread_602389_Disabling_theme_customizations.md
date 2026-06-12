---
title: "Disabling theme customizations"
date: 2007-11-04
forum: Desktop Environments
---

### Post by mskadu on 2007-11-04
Hi,

I have been playing around with desktop customizations and seems I have installed a theme thats making my X hang. Is there anyway I can go back to "as it was my first time logging in" settings?

tia..

---

### Post by Kimmik on 2007-11-04
Press ctrl+alt+fn in the login screen and login, then type:

```


nano /home/YOUR-USER-NAME/.gconf/desktop/gnome/interface/%gconf.xml


```

You can change your themes by editing this file.

---

### Post by mskadu on 2007-11-04
Thanks. I will try that. How about it I want to reset my settings to the default?

---

### Post by Kimmik on 2007-11-04
> **mskadu said:**
> Thanks. I will try that. How about it I want to reset my settings to the default?

I think this is not possible. But you could create a new user accounts with default settings.

---

### Post by mskadu on 2007-11-04
It should be. I tried renaming ~/.config. That seems to have partially achieved this. But there are several others (~/.gnome, ~/.gnome2, ~/.gtk-*, etc). How about those?

.config seems to keep settings for apps (like startup, tracker, etc) so it is not a perfect solution.

---

### Post by Kimmik on 2007-11-04
the .gconf folder contains almost all settings, you could rename it, maybe gnome creates a new one with default settings if you login again.

---

