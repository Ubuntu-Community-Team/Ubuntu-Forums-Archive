---
title: "[Help]Gnome-shell problem...."
date: 2010-12-12
forum: Desktop Environments
---

### Post by zuokun on 2010-12-12
I recently compiled gnome-shell, and tried for few days which seemed very good. So i followed the instruction on the website to change gnome shell as my default session.
Everything was fine until one day, suddenly after I logged into the gnome-shell session, only wallpaper displayed on my desktop, nothing else. I can't do anything with it.

Any idea of what's wrong with my gnome-shell????

thanks in advance

---

### Post by teeedubb on 2010-12-12
Have you tried pressing ALT+F2 and running

```
gnome-terminal
```to open the terminal and then issuing the command

```
dpkg-reconfigure gnome-shell
```to reconfigure the gnome-shell package?

---

### Post by zuokun on 2010-12-12
> **teeedubb said:**
> Have you tried pressing ALT+F2 and running

```
gnome-terminal
```to open the terminal and then issuing the command

```
dpkg-reconfigure gnome-shell
```

to reconfigure the gnome-session package?

yes, i tried, no reaction at all!

---

### Post by Harry33 on 2010-12-12
> **zuokun said:**
> ...
So i followed the instruction on the website to change gnome shell as my default session.
...
Any idea of what's wrong with my gnome-shell????
thanks in advance

Reverse the procedure to setting gnome-shell default. G-S is not so stable, that it would be a good idea to set it as default.
The only good idea is to use package gnome3-session, so that you can choose the desktop from the login screen of the gdm.

Recently there has been problems with mutter and its compatibility with GTK+3 packages. Your issue may also relate to mutter not working fine.

---

