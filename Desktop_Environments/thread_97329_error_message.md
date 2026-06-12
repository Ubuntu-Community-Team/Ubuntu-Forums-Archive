---
title: "error message"
date: 2005-11-30
forum: Desktop Environments
---

### Post by monkblah on 2005-11-30
Hi,
 Using kubuntu 5.10, when I start certain applications like vlc I get a bunch of error messages like this:

```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libxfce.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libxfce.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libxfce.so",
```


etc.

Everything works find but the messages are very annoying.

I do not use the xfce window manager. Why do I get these messages and how can I stop them?

---

### Post by Xian on 2005-11-30
My first thought would be to install the gtk2-engines-xfce package.
The repo it is in is represented below:

```
$ apt-cache policy gtk2-engines-xfce
gtk2-engines-xfce:
  Installed: (none)
  Candidate: 2.3.0cvs20050306-2
  Version table:
     2.3.0cvs20050306-2 0
        500 http://archive.ubuntu.com breezy/universe Packages
```

---

### Post by monkblah on 2005-12-01
[QUOTE=Xian]My first thought would be to install the gtk2-engines-xfce package.
[/QUOTE]

I just installed gtk2-engines-xfce via apt-get but I still get the same error messages when I start VLC. Any other suggestions?

---

