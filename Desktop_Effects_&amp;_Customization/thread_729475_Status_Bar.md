---
title: "Status Bar"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by Zotick on 2008-03-19
IS there any program where I can put a type of status bar on my desktop that shows how much memmory im using, ram, and etc?

---

### Post by sowelie on 2008-03-19
Conky works really well and is very customizable [http://conky.sourceforge.net/]("http://conky.sourceforge.net/").

It's in the repositories too, so you can install it like so::

```
sudo aptitude install conky
```

---

### Post by Iandefor on 2008-03-19
Conky would be a good bet.

[Here's a howto]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html") on installing it/setting it up.

I've found [this thread]("http://ubuntuforums.org/showthread.php?t=281865") to be a good resource for finding good conky configurations.

Here's another [useful conky howto]("http://ubuntuforums.org/showthread.php?t=205865").

And, of course, there is always the [Fine Manual]("http://conky.sourceforge.net/docs.html").

---

### Post by Zotick on 2008-03-19
Okay,  I have it on my desktop but How do I move it and resize it?

---

### Post by Iandefor on 2008-03-20
You have to set its position in .conkyrc. Look in the [manual]("http://conky.sourceforge.net/docs.html"), under "alignment" and "gap_x" and "gap_y" for settings to change in .conkyrc for position.

As for size, the minimum_width and maximum_width settings are also good starting places, as well as xftfont (should have a part that specifies font size).

It's kind of tedious, but .conkyrc is easy to edit. Just open up ~/.conkyrc, edit, and restart conky.

---

