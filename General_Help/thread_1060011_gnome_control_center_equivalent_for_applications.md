---
title: "gnome control center equivalent for applications"
date: 2009-02-04
forum: General Help
---

### Post by lee_connell on 2009-02-04
gnome-control-center brings up a window with preferences and administrations tasks, i seen in opensuse they have one for applications as well, is this available in the repos? If so, what is it called?  I don't see it installed by default.

Thanks!

---

### Post by ibutho on 2009-02-04
If you are referring to YaST which is the openSUSE control center, Ubuntu currently does not have anything similar. It mostly relies on GNOME and KDE system config tools and a few borrowed from elsewhere (some from Fedora), but it does not have something like YaST (Mandriva has something similar called Mandriva Control Center or drakconf and Fedora has a lots of config tools although they are individual apps which are not part of a single control center).

---

### Post by lee_connell on 2009-02-04
I don't believe it's tied to yast in anyway, its identical to gnome-control-center, but instead lists applications. thanks for reply.

---

### Post by ibutho on 2009-02-04
Do you have a screenshot of the application you mean? Is it the SLAB GNOME menu you are referring to? I think posting a screenshot would help you get better responses.

---

### Post by lee_connell on 2009-02-04
[http://farm1.static.flickr.com/72/186544788_5d552f7524_o.jpg](http://farm1.static.flickr.com/72/186544788_5d552f7524_o.jpg)

This link shows the "Application Browser"

Seems to be in 'gnome-main-menu' package: [http://packages.ubuntu.com/jaunty/i386/gnome-main-menu/filelist](http://packages.ubuntu.com/jaunty/i386/gnome-main-menu/filelist)

---

### Post by ibutho on 2009-02-05
The application browser you are referring to is part of the slab menu which was developed by openSUSE. You are correct that its part of the gnome-main-menu package. You need to enable the universe in order to be able to use it. Once installed, right click on the GNOME panel, choose to add a new applet and select gnome-main-menu. If you like SLAB, you may also want to look at the mintmenu from Linux Mint.

---

### Post by lee_connell on 2009-02-05
I don't like slab or mintmenu, just was interested in the application browser, specifically to have an icon for gnome-do's docky that would give quick access to applications using (application-browser) and preferences/administrative tasks (gnome-control-center). This would allow to get rid of the gnome main menu shipped by default.

---

