---
title: "Change the main menu icon"
date: 2007-12-23
forum: Desktop Environments
---

### Post by oddworld on 2007-12-23
I downloaded an icon pack of gnome-look (the black-white one)
[http://gnome-look.org/content/show.php/black-white?content=70299](http://gnome-look.org/content/show.php/black-white?content=70299)

I like it alot, but the main menu icon given isnt very good.
How can I change it?
I read other threads, but none of them were able to help me.

[IMG]http://img341.imageshack.us/img341/1447/97872851bx9.jpg[/IMG]

Thats it right there, not very attractive.

---

### Post by Perpetual on 2007-12-23
The icon is located at /usr/share/icons/Human/scalable/places/.  Once you replace it with the icon of your choice do

```
killall gnome-panel
```

Probably a good idea to rename the old icon just in case you ever decide to use it.

---

