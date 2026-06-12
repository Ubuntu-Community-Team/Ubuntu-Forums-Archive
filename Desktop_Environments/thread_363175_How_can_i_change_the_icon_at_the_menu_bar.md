---
title: "How can i change the icon at the menu bar"
date: 2007-02-16
forum: Desktop Environments
---

### Post by tiptip on 2007-02-16
Hello,
How can i change the icon at the menu bar near "Application Places System" ?
(but keeps the "Application Places System" menu).

I tried to change 
/usr/share/icons/Human/24x24/places/distributor-logo.png
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
but it didnt help :( 

Ubuntu 6.10 + gnome.

[[IMG]http://img508.imageshack.us/img508/3706/screenshot2xg5.png[/IMG]](http://imageshack.us)
[http://img508.imageshack.us/img508/3706/screenshot2xg5.png](http://img508.imageshack.us/img508/3706/screenshot2xg5.png)

---

### Post by wh0rd on 2007-02-16
```
/usr/share/icons/Human/22x22/places/start-here.png
```

---

### Post by tiptip on 2007-02-16
I put a 22x22 icon at /usr/share/icons/Human/22x22/places/start-here.png but it didnt change the icon after i restarted my computer :/

---

### Post by wh0rd on 2007-02-16
Default themes are stored in: /usr/share/icons/Human/22x22/places/start-here.png

NON-Default themes are stored in: /home/**YourUserName**/.icons/**ThemeName**/22x22/places

Make sure you are editing the right theme also.

---

