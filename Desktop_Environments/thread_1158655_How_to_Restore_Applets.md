---
title: "How to Restore Applets"
date: 2009-05-13
forum: Desktop Environments
---

### Post by manolid on 2009-05-13
I was fooling around in 9.04 and removed the Network Manager and Fast User Switch applets from the desktop panel and now can't restore them. 

When i right-click on the panel then select "add to panel", neither one of those applets are shown in the list of available items. 

How can I restore them?    I'm new to Ubuntu and any help will be appreciated

---

### Post by manolid on 2009-05-14
bump

---

### Post by days_of_ruin on 2009-05-14
User Switcher should be there. Type "user" into the search box to find it easier.

Network Manager just pops up in the notification applet.

---

### Post by UbuntuNerd on 2009-05-14
you could try resetting your panels to default, that may bring back all your icons.

---

### Post by manolid on 2009-05-14
All restored. Thanks

---

### Post by kalmichael on 2011-06-30
> **UbuntuNerd said:**
> you could try resetting your panels to default, that may bring back all your icons.How?

---

### Post by Krytarik on 2011-06-30
> **kalmichael said:**
> How?
Enter in the Terminal:
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```Greetings.

---

### Post by AndresC on 2011-09-05
Looks like there is multiple indicator applets in 11.04 and one of them is just the fast switch, there is other with the fast switch plus the date and time and there is what i guess is the unity thing with the menus of the apps.

---

