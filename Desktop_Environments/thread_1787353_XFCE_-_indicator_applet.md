---
title: "XFCE - indicator applet"
date: 2011-06-21
forum: Desktop Environments
---

### Post by hashcode on 2011-06-21
Hello, I can't see in indicator applet things like:

Keyboard layout switcher, Network manager, Bluetooth ...

How can I add them? They are not in standard context menu (properties) of notification area. Thanks

---

### Post by nzjethro on 2011-06-21
Hi there. To get your network manager and bluetooth (or rather your notification area) back, follow [this thread.]("http://ubuntuforums.org/showthread.php?t=527735&page=2")

As for a keyboard switcher, I'm not sure if you can have that on an Xfce panel by default. Look for a plugin called xfce-xkb-plugin ([here you go!]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin#xfce-4.2")). Install this, and add it to your panel, and it'll allow you to switch between keyboard layouts.

---

### Post by hashcode on 2011-06-21
I have notification area in panel and I also have network manager in startup apps

---

### Post by nzjethro on 2011-06-21
Bizarre. I'm not sure what would be causing the issue, but you could try restoring the Xfce panels to their  default layout. To do this, delete the directory
```
~/.config/xfce4/panel
```

---

