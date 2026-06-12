---
title: "login-screen options... gone!!!"
date: 2011-01-21
forum: Desktop Environments
---

### Post by meredith_fer on 2011-01-21
hi everyone...

I was trying to configure x11vnc, and I found out my LOGIN SCREEN SETUP does not have the options it should. Just GENERAL tab... nothing else.

I attached a screenshot so  I may be clearer

any ideas why???

---

### Post by HDave on 2011-01-21
Say hello to GRUB v2.  I also freaked out when I first discovered this.  There is no workaround as far as I know.

---

### Post by ve4cib on 2011-01-21
There are a couple of options you can use to change the look of the login screen:

1- [gdm2setup](https://launchpad.net/gdm2setup).  A relatively simple little program that lets you change the theme of the login page.  It's a little flakey sometimes, but generally does what you need it to do.

2- [ubuntu-tweak](http://ubuntu-tweak.com/).  There's a section dedicated to customizing the login screen.

3- There's some series of commands I can never remember that you can use to change the GTK theme of whatever user it is that owns the login screen (root?).  Someone else can probably provide those.


As for changing the more complicated options... yeah, I can't help you with that.  Sorry.

---

### Post by meredith_fer on 2011-01-21
> **ve4cib said:**
> There are a couple of options you can use to change the look of the login screen:

1- [gdm2setup]("https://launchpad.net/gdm2setup").  A relatively simple little program that lets you change the theme of the login page.  It's a little flakey sometimes, but generally does what you need it to do.

2- [ubuntu-tweak]("http://ubuntu-tweak.com/").  There's a section dedicated to customizing the login screen.

3- There's some series of commands I can never remember that you can use to change the GTK theme of whatever user it is that owns the login screen (root?).  Someone else can probably provide those.


As for changing the more complicated options... yeah, I can't help you with that.  Sorry.

thank you.... but, i need specifically those options so i can enable xdmcp so i can sonfigure vnc

---

### Post by Krytarik on 2011-01-22
Since I don't know exactly what you want to do, take a look at this:
[http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en)

---

### Post by meredith_fer on 2011-01-22
> **Krytarik said:**
> Since I don't know exactly what you want to do, take a look at this:
[http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en)

thank you! i have tried it... but no success :( i do not have installed XMDCP on the system...

---

### Post by Krytarik on 2011-01-22
I've done a further look into the missing XDMCP feature in GDM: Since that is officially removed from GDM, you have to do some considerable work to get it working, if you manage it at all.
Try using one of the other display managers instead: KDM, WDM, XDM. The packages are called the same.

[http://ubuntuforums.org/showthread.php?t=1594697](http://ubuntuforums.org/showthread.php?t=1594697)
[https://bugs.launchpad.net/gdm/+bug/408417](https://bugs.launchpad.net/gdm/+bug/408417)

---

