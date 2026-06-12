---
title: "Compiz Fusion Won't Start with .gtkrc-2.0"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by tprzepiorka on 2007-08-26
Hello,
I followed this guide here to "speed up my gnome menus":
[http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php](http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php)

When I restarted X however compiz fusion now does not start. Here is what I get if I enter "compiz --replace" in the terminal"
```
tprzepiorka1@tprzepiorka-desktop:~$ compiz --replace
/usr/bin/compiz: line 777:  6384 Segmentation fault      (core dumped) $*
/home/tprzepiorka1/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2e00003 specified for 0x3200130 (Changes ap).
```

If I use the Alt-F2 approach to open the windows loose their borders but then come back as they were before.

I think it has something to do with placing the ".gtkrc-2.0" file, but now I can't go and delete it.

Any suggestions?

---

### Post by praet on 2007-08-28
Basically, I would remove the change and try again.
To view hidden files in nautilus try Ctrl+h or alternatively, open a terminal and remove the file that way.

---

