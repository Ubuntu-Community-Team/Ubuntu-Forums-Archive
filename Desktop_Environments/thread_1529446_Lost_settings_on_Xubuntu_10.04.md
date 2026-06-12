---
title: "Lost settings on Xubuntu 10.04"
date: 2010-07-12
forum: Desktop Environments
---

### Post by madmax_haskovo on 2010-07-12
Hi folks.

I have one problem these days: I've installed recently on my Eee PC 901 Xubuntu 10.04 and it works very well, but every time when I logout and then log in again, the desktop drops to the default icons and GTK themes. Then I've figured it out: on logout and then login the XFCE's settings daemon **xfsettingsd** is not loading. It's not so big problem, but it's annoying. Can you tell me how to solve this? Maybe there is a way to autostart this daemon or something... Thanks in advance.

Philip Petev

---

### Post by bobcollard on 2010-07-12
> **madmax_haskovo said:**
> Hi folks.

I have one problem these days: I've installed recently on my Eee PC 901 Xubuntu 10.04 and it works very well, but every time when I logout and then log in again, the desktop drops to the default icons and GTK themes. Then I've figured it out: on logout and then login the XFCE's settings daemon **xfsettingsd** is not loading. It's not so big problem, but it's annoying. Can you tell me how to solve this? Maybe there is a way to autostart this daemon or something... Thanks in advance.

Philip Petev
in Settings/Xfce4 Settings Manager/Session and Startup: check the box for "Automatically save session on logout."

---

### Post by madmax_haskovo on 2010-07-12
> **bobcollard said:**
> in Settings/Xfce4 Settings Manager/Session and Startup: check the box for "Automatically save session on logout."

I did it, but the result was the same :(

---

### Post by bobcollard on 2010-07-12
> **madmax_haskovo said:**
> I did it, but the result was the same :(
Sorry, it worked for me.  Perhaps someone else can help?

---

