---
title: "quick gnome panel question"
date: 2009-03-12
forum: Desktop Environments
---

### Post by fooey on 2009-03-12
Is there a way to only make a window show up in the "notification area" of the panel and NOT the Window List ?

I know you can use Alltray or something to minimize to the notification area, but when you restore that window the window list is shown again. Just wondering..  Thanks..

---

### Post by cph05a on 2009-03-12
see if this helps:

[http://svn.gnome.org/viewvc/zenity/trunk/src/notification.c?view=markup](http://svn.gnome.org/viewvc/zenity/trunk/src/notification.c?view=markup)

---

### Post by fooey on 2009-03-12
Hrm. How would I go about using that source in terms of what I'm trying to do?

---

### Post by mcduck on 2009-03-13
If you use Compiz, you can use the Window Rules-plugin to configure a program to not show in the window list. But it will not help you in getting the program to use notification area, you need to use something else for that.

---

