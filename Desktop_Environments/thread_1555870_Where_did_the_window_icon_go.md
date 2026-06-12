---
title: "Where did the window icon go?"
date: 2010-08-18
forum: Desktop Environments
---

### Post by ygoe on 2010-08-18
On most modern Gnome and MS Windows systems, each window has a window menu in the top (left) corner, which shows the window icon. In my Ubuntu 10.4, there's no icon but a small black radio bullet instead. (I already moved the button order to a more traditional one: "menu:minimize,maximize,close") How can I get the window icon back there? I've tried the word "icon" instead of "menu" but that's not recognised.

---

### Post by xangua on 2010-08-18
use another metacity theme or edit your current metacity config file

---

### Post by ygoe on 2010-08-19
Thanks for the direction to look. I hoped for an easier solution, but I now managed to make a copy of Radiance and use some parts of the ClearLooks theme regarding the <button function="menu"...> elements. Works as expected. I also could set the default button order so I don't have to change it later again.

---

