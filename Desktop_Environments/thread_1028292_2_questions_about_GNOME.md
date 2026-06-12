---
title: "2 questions about GNOME"
date: 2009-01-02
forum: Desktop Environments
---

### Post by Fzang on 2009-01-02
1. How do I center the application icon like this?

[IMG]http://i39.tinypic.com/w6yr6v.png[/IMG]


2. How do I make the gnome panel completely transparent? I can only make the empty part of the panel transparent but system tray, volume icon and clock stays opaque system color

---

### Post by gjoellee on 2009-01-02
> **Fzang said:**
> 1. How do I center the application icon like this?

[IMG]http://i39.tinypic.com/w6yr6v.png[/IMG]


2. How do I make the gnome panel completely transparent? I can only make the empty part of the panel transparent but system tray, volume icon and clock stays opaque system color

1. Isen't it like that by default? If not I am sure you can find something in the gkonf editor ```
gkonf-editor
```

2. Right click on the panel and find look..

(sorry I don't use GNOME any more so I don't remember this so well, but panel transparency is easy and graphical turned on. Just right click and check things out)

---

### Post by cdtech on 2009-01-02
Try this site:
[http://www.linuxselfhelp.com/gnome/users-guide/index.html](http://www.linuxselfhelp.com/gnome/users-guide/index.html)

---

### Post by tuxxy on 2009-01-02
> **Fzang said:**
> 
2. How do I make the gnome panel completely transparent? I can only make the empty part of the panel transparent but system tray, volume icon and clock stays opaque system color

You could install emerald theme manager and download the required theme from [http://gnome-look.org](http://gnome-look.org) or simply edit your current theme  to be transparent.

```
sudo apt-get install emerald
```

You may need to run the comand below to run emerald and also you could add it to your sessions to prevent needing to run it every bootup.
```

emerald --replace
```

---

