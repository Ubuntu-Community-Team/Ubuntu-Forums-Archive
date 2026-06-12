---
title: "gnome theme changing constantly!"
date: 2007-06-01
forum: Desktop Environments
---

### Post by erkka on 2007-06-01
this seems weird enough to me,

We have Dapper, and GNOME is OK with my account,
but when my wife logs in, GNOME goes wild, it keeps
on changing the desktop theme constantly, on its own,
randomly, automatically and all the time, and I cannot
find a way to make it stop!

This happens even if she logs in using failsafe-gnome.

I tried to scan the system with top / system monitor,
and it says that gnome-settings-manager is running.
I tried to kill it but it won't die.
I open the settings-manager, and it complains that
an other setting-manager is conflicting with it,
but it opens anyway and all the settings are OK,
and if I manually select a theme, it does nothing.

it is very frustrating to try to work with it
because the screen is flickering, fonts changing,
icons jumping etc...

why is this?
is there some user-specific setting-files and
where can i look for them? 

anyone else ever experienced this?

-Erkka

---

### Post by greybirds on 2007-06-01
I'm assuming you've tried System > Preferences > Theme and set it to something sane.

This might provide a bit more information.

Type gconf-editor in a terminal. This is where a lot of Gnome's user settings are stored. A window with left and right panes should open up. In the left pane, you will see a tree of categories and subcategories. The right holds lists of names and values for the selected category.

Open up "/", then "desktop", "gnome" (the one under desktop, not "Gnome" further down), and finally click "interface" (there won't be a triangle beside it.

The right pane will be populated with names and values paired up. Scroll through and find the names "gtk_theme", "icon_theme", and "font_name" and print their values here. That could be helpful in deciding what's going wrong.

---

### Post by erkka on 2007-06-01
gtk-theme   Human
icon-theme  Human
font-name   Sans 10

I also checked with my own account, and the settings are the same.

Then I tried to delete directoried .gnome, .gnome2,
.gconf, .gconfg and .metacity from my wifes home-directory
but that does not help.

-Erkka

---

