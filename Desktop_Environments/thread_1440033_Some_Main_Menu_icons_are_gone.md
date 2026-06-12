---
title: "Some Main Menu icons are gone"
date: 2010-03-27
forum: Desktop Environments
---

### Post by jscoobyced on 2010-03-27
On my "Main Menu" applet, when I installed Ubuntu there were all icons displayed in front of each items. Now I am missing some icons, but only under the "Places" and "System" menus (and their sub-menus). Under those menus, the lowest level (the applications) still have their icon though.
When I go to "Edit Menu" the icons are showing in the Edit Menu interface.
Before I try to remove .gnome* and .gconf* from my home directory, anything I could check?

Thanks,
JSC

---

### Post by mcduck on 2010-03-27
That's normal, many of the menu icons are disabled in Ubuntu 9.10 and later (might have been 9.04, I'm not absolutely sure).

Anyway, nothing is broken so don't try too hard to fix it.. :D

(if you want to have all the icons enabled, open gconf-editor and enable the *desktop/gnome/interface/menus_have_icons* -key.)

---

### Post by jscoobyced on 2010-03-27
Thanks. That's what I needed (gconf-editor). The odd thing is that I have been using Ubuntu since 9.04 on my laptop. When 9.10 came I did a fresh install (I kinda screwed up the upgrade-dist) and the icons where all here. Probably from my home folder which was kept from 9.04.

---

### Post by lantolin on 2010-04-14
Hi,

tanks for the post, I was having exactly the same behavior in some of my debian squeeze boxes after an upgrade.

I went crazy trying to diagnose it and fix it. It is fixed now.

Just to point that in my system is not necesary to go down to gconf-editor, there is a nice setting for it in Preferences -> Appearance -> Interface Tab -> Show Icons in menus

R,

   /Luis

---

### Post by Smartflight on 2010-11-23
Thanks!

That helped

---

