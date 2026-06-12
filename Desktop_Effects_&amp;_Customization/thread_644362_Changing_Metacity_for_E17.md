---
title: "Changing Metacity for E17"
date: 2007-12-18
forum: Desktop Effects &amp; Customization
---

### Post by ataide.carlos on 2007-12-18
Hi guys!

I'm looking for a way of changing Metacity for E17 under Gnome.
I like the functionality in Gnome, but there are some parts of E17 that I would like to use also. Running Enlightenment solo is not yet an option. The File Manager is kinda sucky, and only the minimized windows show in the list. 
How can I use both??

---

### Post by ajmorris on 2007-12-18
Hi there,
The easiest way to do this is the new ubuntu project called geubuntu. It combines the power of gnome with the slickness of Enlightenment. Head on over to [http://geubuntu.intilinux.com/](http://geubuntu.intilinux.com/) to check it out.
Its a very good project.

---

### Post by ataide.carlos on 2007-12-19
Hi,

That is definitely a distro that I will check, but for now I would like to try to do it myself. Mostly because I want the learning experience too :)

---

### Post by smartboyathome on 2007-12-22
I would say just log into e17 and then start up gnome-settings-daemon and gnome-session (the last one you can do if you want, and adds basically a full gnome install minus metacity). I find it better than just using E17 in GNOME since it is running without the bloat.

---

### Post by scubajeff on 2007-12-23
If you mean you want your lovely gtk theme to show in E17, then a easy way to do this is to create the file ~/.gtkrc-2.0, so that GTK base program can be decorated. Mine look like this:

```

include "/usr/share/themes/Outdoors/gtk-2.0/gtkrc"
gtk-font-name = "Serif 9"
gtk-icon-theme-name = "Tango"

```

---

