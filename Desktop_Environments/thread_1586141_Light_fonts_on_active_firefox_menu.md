---
title: "Light fonts on active firefox menu"
date: 2010-10-01
forum: Desktop Environments
---

### Post by infected?! on 2010-10-01
Hi!

Sorry if i am posting in the wrong forum but i dont found any bug section.

I recently tested ubuntu 10.10 rc and would like to report a "cosmetic thing". If i use the new radiance theme and click on a menu point in firefox the fontcolor of the active menupoint changes to white on a silver or light grey background which is not easy to read. The submenu is displayed well because of the orange hover effect. How can i fix this?

---

### Post by hhh on 2010-10-01
You can use a userchrome.css file to fix it...
[http://kb.mozillazine.org/UserChrome.css](http://kb.mozillazine.org/UserChrome.css)

Try adding this to the bottom of it...
```
.menubar-text,
menubar > menu[_moz-menuactive="true"] {
  color: inherit !important;
}
```
If that doesn't work, try switching color: inherit !important for a specific color or hex-code, like...
```
.menubar-text,
menubar > menu[_moz-menuactive="true"] {
  color: black !important;
}
``` or ```
.menubar-text,
menubar > menu[_moz-menuactive="true"] {
  color: #1F1F1F !important;
}
```

---

### Post by infected?! on 2010-10-01
Well, that could work (i can´t test it now) but i think it´s better to fix it in the ubuntu theme itself (if possible).

---

