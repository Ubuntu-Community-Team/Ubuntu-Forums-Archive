---
title: "application menu configuration"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by sycamorex on 2007-06-11
Hi,

I must have done something and I lost the system tools entry in Applications menu in gnome (Ubuntu feisty fawn). How can I restore it?

thanks

---

### Post by 67GTA on 2007-06-11
Right click on the panel menu button, click on "edit menu" and look for the system tools entry, and make sure it is checked. You might also try "update-menu" in a terminal.

---

### Post by sycamorex on 2007-06-11
Thanks,

When I try to tick the system tools entry (right-click -> edit menus), it unticks itself automatically after one second.

I don't seem to have update-menu installed - when I type it, it says that command not found.

> 
root@ubacer:/etc# apt-get install update-menu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update-menu

thanks

---

### Post by 67GTA on 2007-06-11
It sounds like you don't have anything in the system tools menu. You have to have something like "file browser" or "configuration editor" checked inside of the "system tools" menu for it to show, or it will do that.

---

### Post by sycamorex on 2007-06-11
That was it, thanks

---

