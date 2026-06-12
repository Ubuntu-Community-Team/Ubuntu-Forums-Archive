---
title: "guake broke"
date: 2011-01-04
forum: Desktop Environments
---

### Post by anystupidname1 on 2011-01-04
Guake just suddenly broke (tries to launch for 5 seconds and disappears)
I tried tilda for 10 minutes and it managed to steal my keyboard and crash
Yakuake requires 210MB of KDE dependencies
Can anybody suggest a better substitute please?

---

### Post by earlycj5 on 2011-01-04
> **anystupidname1 said:**
> Guake just suddenly broke (tries to launch for 5 seconds and disappears)
I tried tilda for 10 minutes and it managed to steal my keyboard and crash
Yakuake requires 210MB of KDE dependencies
Can anybody suggest a better substitute please?

Errors when launching Guake from another terminal session could be helpful.

Still working great for me on all of my machines.

---

### Post by anystupidname1 on 2011-01-05
Thanks for the interest. This is happening on two out of six machines I have configured similarly. Although, this one is 64bit and the other one is 32bit... Seems fishy that both happened at same time.

> (guake.py:27185): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Traceback (most recent call last):
  File "/usr/lib/guake/guake.py", line 1353, in <module>
    if not main():
  File "/usr/lib/guake/guake.py", line 1296, in main
    instance = Guake()
  File "/usr/lib/guake/guake.py", line 620, in __init__
    self.add_tab()
  File "/usr/lib/guake/guake.py", line 1137, in add_tab
    final_params = self.get_fork_params(default_params)
  File "/usr/lib/guake/guake.py", line 1086, in get_fork_params
    self.update_proxy_vars()
  File "/usr/lib/guake/guake.py", line 1102, in update_proxy_vars
    ssl_port = self.client.get_string('/system/proxy/secure_port')
glib.GError: Type mismatch: Expected `string' got `int' for key /system/proxy/secure_portTried "sudo aptitude reinstall gtk2-engines" and "gconftool-2 --install-schema-file=/usr/share/gconf/schemas/guake.schemas
" and a couple other things. Is there a PPA I could add for gtk2-engines-ubuntulooks to be available in maverick for reinstall attempt?
I'll see if the 32bit box is throwing the same error.

---

### Post by anystupidname1 on 2011-01-05
32bit box:
> Traceback (most recent call last):
  File "/usr/lib/guake/guake.py", line 1353, in <module>
    if not main():
  File "/usr/lib/guake/guake.py", line 1296, in main
    instance = Guake()
  File "/usr/lib/guake/guake.py", line 620, in __init__
    self.add_tab()
  File "/usr/lib/guake/guake.py", line 1137, in add_tab
    final_params = self.get_fork_params(default_params)
  File "/usr/lib/guake/guake.py", line 1086, in get_fork_params
    self.update_proxy_vars()
  File "/usr/lib/guake/guake.py", line 1102, in update_proxy_vars
    ssl_port = self.client.get_string('/system/proxy/secure_port')
glib.GError: Type mismatch: Expected `string' got `int' for key /system/proxy/secure_port

Almost identical. Hmmmm

---

### Post by earlycj5 on 2011-01-06
Looks like something with SSL or glib to me, not the theme.

---

### Post by arti74 on 2011-01-08
Solution in my archlinux was to downgrade libknotify to version libnotify-0.4.5-1.1-i686.pkg.tar.gz 
If that won't work try this maybe [http://guake.org/ticket/246](http://guake.org/ticket/246).
Hope something helps you too ;)

---

