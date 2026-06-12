---
title: "Can't get to firefox through the menus"
date: 2009-01-07
forum: General Help
---

### Post by slwory on 2009-01-07
I booted into Ubuntu after a long time today and decided I didn't wanna use the FF3.1b - I wanted the FF 3.0 instead. So I deleted the FF folder in the Opt folder and uninstalled FF through synaptic manager. Then I reinstalled it.

Going through terminal I can type Firefox-3.0 and it will launch but when I go Applications -> Internet -> Firefox I get the error "Could not launch menu item. Failed to execute child process "Firefox" (No such file or directory)".

So how can I fix this?

---

### Post by namdung on 2009-01-07
In *System==>Pref==>Main Menu==>Applications==>Internet*, *Right click==>Properties* and check what is in the *Command* field. You may change it to **Firefox** or **Firefox-3.0**.

---

### Post by cariboo on 2009-01-07
Can you start Firefox from a terminal? If so then you should be able to set up a menu item for Firefox.

Right click on Applications and select Edit Menus. Highlight Internet-->Firefox Web Browser, right click and select properties.In the Command Box click browse and navigate to /usr/bin/firefox and click ok. then click close. You should now be able to launch Firefox from the menu.

Jim

---

