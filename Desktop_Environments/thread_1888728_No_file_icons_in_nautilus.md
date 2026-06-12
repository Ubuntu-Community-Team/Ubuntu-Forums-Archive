---
title: "No file icons in nautilus"
date: 2011-11-29
forum: Desktop Environments
---

### Post by robot682 on 2011-11-29
Hello,

I have this weird issue, while using the Awesome Window Manager, where files do not have icons when displayed in Nautilus or.  What I mean is that files and folders all have the blank page icon.

When I use the Unity desktop the icons display correctly.

I would appreciate any help.

Thanks.

---

### Post by robot682 on 2011-11-30
As an update, I get the following errors when I run nautilus.

```
(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:18877): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:18877): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed
```

Not sure if that helps.

---

### Post by dFlyer on 2011-11-30
> **robot682 said:**
> Hello,

I have this weird issue, while using the Awesome Window Manager, where files do not have icons when displayed in Nautilus or.  What I mean is that files and folders all have the blank page icon.

When I use the Unity desktop the icons display correctly.

I would appreciate any help.

Thanks.

What version of ubuntu are you running 11.04 or 11.10?

---

### Post by robot682 on 2011-11-30
I am running 11.10.

---

### Post by fredrik hansson on 2011-12-01
I have exactly the same issue, but I'm using OpenBox not Awsome.
Nautilus looks good in Unity. I'm also on 11.10.
I hope someone can help me.

(I also have this problem when I use themes other than "Humanity": [https://bugs.launchpad.net/ubuntu/+source/catfish/+bug/669572](https://bugs.launchpad.net/ubuntu/+source/catfish/+bug/669572) is it related?)

---

### Post by kounoupis on 2011-12-02
rm -rf ~/.cache

logout/login.

That fixed it for me.

You should be able to identify specifically what inside .cache causes the problem and delete that folder, but I found it easier to just delete the whole thing and move on with my life...

---

### Post by fredrik hansson on 2011-12-03
> **kounoupis said:**
> 
rm -rf ~/.cache
logout/login.


Thank you. I'm away over the weekend. Will try as soon as I'm home.

Edit: Didn't work... Thanks for the suggestion.

---

### Post by robot682 on 2011-12-05
> **kounoupis said:**
> rm -rf ~/.cache

logout/login.

That fixed it for me.

You should be able to identify specifically what inside .cache causes  the problem and delete that folder, but I found it easier to just delete  the whole thing and move on with my life...


I really appreciate everyone trying to help. I just tried this and it did not work for me.

---

### Post by jcanini on 2012-01-23
I had a similar problem after upgrading to 11.10. (My custom icons remained but all others were a generic icon, so folders, files, mounted file systems etc all looked the same)

sudo apt-get install gnome-tweak-tool

Fixed it for me... 

after trying various other methods inc the one above and rm .local/share/gvfs-metadata/*.

got this soloution from 
[http://askubuntu.com/questions/93329/how-can-i-change-my-nautilus-and-icon-themes-back-to-what-i-had-before](http://askubuntu.com/questions/93329/how-can-i-change-my-nautilus-and-icon-themes-back-to-what-i-had-before)

---

