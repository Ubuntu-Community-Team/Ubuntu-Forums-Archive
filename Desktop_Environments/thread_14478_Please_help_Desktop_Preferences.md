---
title: "Please help Desktop Preferences"
date: 2005-02-07
forum: Desktop Environments
---

### Post by rdking on 2005-02-07
Ok So after an update of some gnome packages, I discovered that my desktop preferences had moved from the menu "Computer" over to the menu Applications.  Me being a perfectionist, liked them where they were originally...so I googled, and found a site claiming to have a work around.  Unfortunately, I followed it and believe that I have deleted the menu itemsfrom ///:Applications.  Have tried to synaptic and re-install all the gnome base sytem but no desktop preferences....can someone help me get them back!

Is reinstalling ubuntu neccessary?

---

### Post by alastair on 2005-02-07
This stuff gets me as well sometimes - but I think things are (overall) a LOT more sane than they used to be a few years ago.

I would try - make a new user , log out (to GDM) and log in as the new user. If this user has the settings you like, you might get away with just copying their ~/.gnome2 directory on top of yours. Then log out and log in as yourself ...

Worth a try, if all else fails. I assume there's a straightforward way to deal with panel menu's alone though.

---

### Post by Ironi on 2005-02-07
[QUOTE=rdking]I googled, and found a site claiming to have a work around. Unfortunately, I followed it and believe that I have deleted the menu itemsfrom ///:Applications. Have tried to synaptic and re-install all the gnome base sytem but no desktop preferences....can someone help me get them back!
   [/QUOTE]
 Do you have a link to the site? Without that, I have no way of knowing whether what I'm going to tell you is even going to work...
   
   > Is reinstalling ubuntu neccessary?
 Not even close. My guess is that you played around with /etc/xdg/menus/applications.menu ... with that assumption, here's how you restore it:
   
   1. Grab a .deb for [Ubuntu's gnome-menus]("http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/") or [Debian's kdelibs-data](http://http.us.debian.org/debian/pool/main/k/kdelibs/kdelibs-data_3.3.2-1_all.deb) package. I recommend kdelibs-data; its applications.menu is much better organized.
   
   2. Extract and copy applications.menu like so:
   [b]dpkg-deb -x [package] /tmp/menus
   cp /tmp/menus/etc/xdg/menus/applications.menu /etc/xdg/menus[/b]
   
   3. **update-menus**

---

