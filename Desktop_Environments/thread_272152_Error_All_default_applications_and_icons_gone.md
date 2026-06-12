---
title: "Error: All default applications and icons gone"
date: 2006-10-05
forum: Desktop Environments
---

### Post by TheMono on 2006-10-05
Ok, this one is a little odd. I installed today's updates - openssl and something else.... And MonoDevelop from [www.getdeb.net](www.getdeb.net), and now all my default applications and icons are gone.

Meaning, Say I have a deb package on the desktop. It no longer knows to open that with GDebi, and it now has the generic Gnome foot icon. As do my PDF's, which no longer know of Evince or Adobe, my doc's which have lost OpenOffice, my ppt's have lost it too, etc.

It's quite odd really, though it is obviously very annoying.

Any help would be great.

---

### Post by brt on 2006-10-05
one way to restore all of your gnome settings is to remove your gnome folders in your homedirectory, as it will be populated with the defaults upon next logon.

the cleanest way is to logout, logon as a different user or <ctrl><alt><F1> to logon to the console and do:

> cd /home/<username>
mv .gconf .gconf.old
mv .gnome .gnome.old
mv .gnome2 .gnome2.old

logout and/or <strg><alt><F7> and log back in as usual and you should have all default gnome-settings again including your panels, menu, desktopbackground...

---

### Post by TheMono on 2006-10-05
Ech... Efficient, if a little brute force lol. Given the amount of customisation that has gone into some of my Gnome settings, that might not be the best way to do it...

You don't happen to know which file stores the defaults for icons and for which application to handle things with? Because I will try with moving those rather than bulk all the gnome settings. Thanks for the idea though.

---

### Post by linuxrevo on 2007-12-14
Ya! I had this problem too. I just did like this:
Right click on desk top and choose **Change desktop background**, then go to** Interface tab**, Uncheck** Show icons in menus** and after it, check it again... 
My problem has been solved.

---

