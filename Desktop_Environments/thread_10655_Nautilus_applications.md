---
title: "Nautilus applications:///"
date: 2005-01-09
forum: Desktop Environments
---

### Post by relux on 2005-01-09
I am trying to edit my gnome menus. I can not seem to. It seems the correct way or the ideal way to do it is to simply browse to applications:/// in Nautilus.  I am unable to do this. I get the following error:

applications:/// is not a valid location.
Please check the spelling and try again.

Any insight?

---

### Post by wallijonn on 2005-01-09
It didn't work for me.

The only thing I did to make it work was to right click the double bar between the lower left bottom desktop icon and the first window (double row of dots), Preferences, set "Always Group Windows", closed.

Then for some reason applications:/// works. weird. I was also working on /etc/fonts/font.conf and .fonts/font.conf. But this was before I played with the 'Always Group Windows" setting. 

Can't you go to the menu and right click an application and delete? Although it is easy to cut and paste from one menu to another; and I figure that this is what you want to do.

---

### Post by relux on 2005-01-10
hrm, that is weird. They have absolutely nothing to do with each other.  I did try it however and applications:/// still did not work.  I do not have the option to remove from the menu if I right click...

---

### Post by wallijonn on 2005-01-10
Applications -> System Tools -> Configuration Editor -> 
/apps/panel/profiles/default/objects/object_0/menu_path
/apps/panel/profiles/default/objects/menu_bar/menu_path
/apps/panel/profiles/default/objects/object_1/menu_path
/apps/panel/profiles/default/objects/firefox_launcher/menu_path
/apps/panel/profiles/default/objects/object_2/menu_path
/apps/panel/profiles/default/objects/object_3/menu_path
/apps/panel/profiles/default/objects/object_4/menu_path
/apps/panel/profiles/default/objects/object_5/menu_path
/apps/panel/profiles/default/objects/nautilus_launcher/launcher_location
/apps/panel/profiles/default/objects/evolution_launcher/menu_path
/apps/panel/profiles/default/applets/workspace_switcher/menu_path
/apps/panel/profiles/default/applets/window_list/menu_path
/apps/panel/profiles/default/applets/trashapplet/menu_path

Each of the menu/object should relate to an application.

Did you try loging out & back in? The Computer -> Home, address bar -> applications:/// ?

This one I am interested in finding out, jst like finding out where my burners are defined (so that I can make gnomeBaker work).

---

