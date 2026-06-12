---
title: "GTK2 ubuntulooks theme engine error"
date: 2010-05-11
forum: Desktop Environments
---

### Post by vockleya on 2010-05-11
I have a custom theme I downloaded from gnome-looks (overglossed, if you want to know), and I am getting an error every time I start a GTK application from terminal. This started after I upgraded from 9.10 to 10.04.

```
Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks"
```I have tried installing gtk2-engines-ubuntulooks, but apt says there is no installation candidate. Any ideas?

---

### Post by pspolito on 2010-07-12
I had this problem in my recently updated 10.04 Lucid:

Unable to locate theme engine in module_path: "ubuntulooks",

when launching many apps such as gedit. After I installed this:

[http://launchpadlibrarian.net/15789446/gtk2-engines-ubuntulooks_0.9.12-12_amd64.deb](http://launchpadlibrarian.net/15789446/gtk2-engines-ubuntulooks_0.9.12-12_amd64.deb)

the problem is gone.

I hope it helps.;)

Polito

---

