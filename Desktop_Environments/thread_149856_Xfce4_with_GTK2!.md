---
title: "Xfce4 with GTK2!"
date: 2006-03-24
forum: Desktop Environments
---

### Post by VaDor on 2006-03-24
hi all,

I have installed the Xubuntu. But When I enter in the Xfce I haven't gtk2 so every window will  glue at the top. I have the gtk2-engine-xfce installed etc..

What can I do to force Xfce4 use gtk2 engine?


Thks all

---

### Post by helpme on 2006-03-25
[QUOTE=VaDor]hi all,

I have installed the Xubuntu. But When I enter in the Xfce I haven't gtk2 so every window will  glue at the top. I have the gtk2-engine-xfce installed etc..

What can I do to force Xfce4 use gtk2 engine?


Thks all[/QUOTE]
From your description it doesn't sound as if it's a gtk2 problem, but as if no window manager is running. That is, there are no borders around your applications and you are for example unable to move your windows. 

If this is your problem, it seems that xfwm4, the xfce windowmanager is not running. The first thing you should do is check if you can get it to run by opening a terminal and running xfwm4 &
If this works, save your session, so that it will get started in the future automatically, if it doesn't work, post any error message you get here.

---

