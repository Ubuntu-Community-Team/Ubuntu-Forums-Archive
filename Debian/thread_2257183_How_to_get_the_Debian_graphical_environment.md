---
title: "How to get the Debian graphical environment"
date: 2014-12-17
forum: Debian
---

### Post by Deepesh_Thapa on 2014-12-17
[COLOR=#333333][FONT=Lucida Grande]Dear all,

[/FONT][/COLOR]sorry i could not find any answer about linux distro besides this forum.

[COLOR=#333333][FONT=Lucida Grande]I recently installed debian 7.7.0 i386 on my virtual machine in windows... The installation went well and i think I forgot to check the graphical desktop environment during installation. Now after installation i come up with the Linux command line, Could anybody tell me how to get the desktop graphical environment without re installing please..[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Many thanks[/FONT][/COLOR]

---

### Post by lukeiamyourfather on 2014-12-17
See the Debian documentation for various desktop environments.

[https://wiki.debian.org/DesktopEnvironment](https://wiki.debian.org/DesktopEnvironment)

Here's an example of how to install GNOME (from the page about GNOME on the link above).

```
apt-get install aptitude tasksel
tasksel install gnome-desktop --new-install
```

Note you don't have to install tasksel for each desktop environment, just for the first one installed.

---

