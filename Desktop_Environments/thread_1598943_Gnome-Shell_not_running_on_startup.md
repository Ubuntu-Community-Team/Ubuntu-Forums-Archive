---
title: "Gnome-Shell not running on startup"
date: 2010-10-17
forum: Desktop Environments
---

### Post by Lazaruss on 2010-10-17
Running Maverick, I have installed gnome shell - I attempted to use the build process, but repeated failures meant I had to use the Ubuntu Repo version.

Every time I startup ubuntu, with gnome-shell set in gconf: /desktop/gnome/session/required_components/windowmanager, I am left with no gnome shell, and a white desktop.

There is usually a window manager running - I have window titles, borders, close buttons etc, and should i enter gnome-shell into terminal, I am told a window manager is already running.

I can get gnome-shell back by using gnome-shell --replace.

Using dmesg, I have a message which reads

```
[ 5372.307463] mutter[27710]: segfault at 8 ip 01acaa13 sp bfb52154 error 4 in libgnome-shell.so[1aa9000+65000]
```

I am using Ubuntu 10.10, running a Gnome 3 Session, on an Acer Aspire 5100 Laptop

---

### Post by Lazaruss on 2010-11-23
bump

---

