---
title: "Help Installing xfce4-timer-plugin"
date: 2007-03-12
forum: Desktop Environments
---

### Post by racyrefinedraj on 2007-03-12
I am trying to install a [Timer Plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-timer-plugin) on my new shiny XFCE desktop like I once had on my slow but otherwise nice gnome desktop. The website says that there are no dependencies in addition to XFCE, but when I try a "sudo ./configure" I get the following (trimmed for sanity): 

```

...
checking for gthread-2.0 >= 2.4.0... 2.10.3
checking GTHREAD_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking GTHREAD_LIBS... -pthread -lgthread-2.0 -lglib-2.0
checking for gtk+-2.0 >= 2.4.0... not found
*** The required package gtk+-2.0 was not found on your system.
*** Please install gtk+-2.0 (atleast version 2.4.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

```

If I am reading this right it says I don't have the proper version of gtk+ installed. Really I have no Idea how to check whether or not I have the right version... which of the many gtk packages is it looking at exactly? If I do "apt-cache search  gtk+-2.0" I get no results. Could someone give me some guidance? I'm on Dapper, by the way

---

### Post by racyrefinedraj on 2007-03-12
For what it's worth, I figured it out. Needed the Dev packages for GTK and XFCE... duh. I just wish that these error messages would be better at telling me what packages I need... (and maybe just asking me if I wanna apt-get them? Sheesh, that'll be the day)

Much respect to the folks in #xfce that helped me out.

---

