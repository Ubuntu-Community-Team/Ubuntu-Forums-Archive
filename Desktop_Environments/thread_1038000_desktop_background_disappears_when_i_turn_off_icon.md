---
title: "desktop background disappears when i turn off icons"
date: 2009-01-12
forum: Desktop Environments
---

### Post by Mr.Krinkle on 2009-01-12
like the title says. how can i fix it? here are pics to help

icons enabled 
[[IMG]http://img255.imageshack.us/img255/6371/desktop1wp2.th.jpg[/IMG]](http://img255.imageshack.us/my.php?image=desktop1wp2.jpg)

icons disabled
[[IMG]http://img205.imageshack.us/img205/6641/desktop2pl0.th.jpg[/IMG]](http://img205.imageshack.us/my.php?image=desktop2pl0.jpg)

---

### Post by Magical Tiger on 2009-09-12
What are you using to turn off the icons? I use the following and it works: ```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
``` 
PS: Sorry for the late reply

---

