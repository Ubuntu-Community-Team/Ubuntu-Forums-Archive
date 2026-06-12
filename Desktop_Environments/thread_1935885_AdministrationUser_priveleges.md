---
title: "Administration/User priveleges"
date: 2012-03-05
forum: Desktop Environments
---

### Post by H3110 on 2012-03-05
Hi All,

I have been doing lot's of searching around Google and this forum particularly, for information about removing some features. If anyone could help me either with my search for tutorials, posts or even instructions it would be most appreciated.

I have installed Ubuntu 11.10 - Gnome-Shell, I would like to remove the following items:

1. On the login-screen, the COG/Theme menu on the user list (So nobody can change the theme from Gnome).

2. The power-options from the top-right corner (So nobody can suspend, hibernate, restart or reboot. Although I could sudo reboot via terminal if I wanted of course).

So far i have tried:

```
$ sudo dconf-editor
```
```
$ sudo apt-get install dconf-tools -y && sudo dconf-tools
```

following instructions to "disbale power-options" after a reboot nothing has changed.

Thanks.

---

