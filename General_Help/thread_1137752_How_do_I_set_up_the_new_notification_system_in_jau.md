---
title: "How do I set up the new notification system in jaunty?"
date: 2009-04-25
forum: General Help
---

### Post by josephellengar on 2009-04-25
When I try to put the new notification applet on the gnome-bar, nothing shows up at all.  And there aren't any options on my gnome menu.

---

### Post by joeyknuccione on 2009-04-26
> **idigchess said:**
> When I try to put the new notification applet on the gnome-bar, nothing shows up at all.  And there aren't any options on my gnome menu.
Make sure you are using the "official" realease, and not the candidate. Also, do:

System > Preferences > Pop-up Notifications

If it still doesn't show up, try:

System > Preferences > Main Menu, and look for it there

---

### Post by NESFreak on 2009-04-26
> **joeyknuccione said:**
> Make sure you are using the "official" realease, and not the candidate. Also, do:

System > Preferences > Pop-up Notifications

If it still doesn't show up, try:

System > Preferences > Main Menu, and look for it there

it didn't make it to the final

---

### Post by josephellengar on 2009-04-26
> **joeyknuccione said:**
> Make sure you are using the "official" realease, and not the candidate. Also, do:

System > Preferences > Pop-up Notifications

If it still doesn't show up, try:

System > Preferences > Main Menu, and look for it there

When I did the upgrade it didn't install the notify-ocd package.  That was the problem.

---

### Post by buddywilliams on 2009-04-28
> When I did the upgrade it didn't install the notify-ocd package. That was the problem.

I think he meant to say: notify-osd

Also, if you don't have System > Preferences > Pop-up Notifications, then you can right click on the menus > Edit Menu, then under the menu editor: System > Preferences > check the Pop-up Notifications menu item. I should warn you that the options are meager at best because it doesn't allow you to specify which notifications to allow.

---

