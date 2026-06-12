---
title: "Top Panel Problem"
date: 2009-06-08
forum: Desktop Environments
---

### Post by Link9rly on 2009-06-08
Hello. I am new to Ubuntu ( I got it last Saturday). I have a big problem as of now. I had it and started experimenting around and came across the idea of making it look like a mac. I don't remember which step I stopped at, but when I logged off, there was some error flashing. screen isn't composited, if I'm correct. I don't know what I did to it, but the top panel is flashing madly and there is no way to stop it. Worse than that is AWN won't come up and I can't use any program since every program had a launcher on AWN :o . So now, I can't do nothing except stare in shame at the top panel. Is there any way to reset the panel and everything to normal with no reinstall? I just want to reset the theme, and top panel.

---

### Post by cyfur01 on 2009-06-08
Check out this: [ How to Reset Ubuntu Gnome Settings to Defaults]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

---

### Post by UbuntuNerd on 2009-06-08
type this in a terminal:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by Link9rly on 2009-06-14
Ok. I don't know the terminal shortcut, but when I try the alt f2 shortcut to run something, it flashes and dissapears. I uploaded a vid so you can see what happens.

[http://www.youtube.com/watch?v=OYCbxXGsoEs](http://www.youtube.com/watch?v=OYCbxXGsoEs)

---

