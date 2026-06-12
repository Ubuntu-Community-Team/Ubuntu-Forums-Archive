---
title: "gnome fallback issue - plz help"
date: 2012-02-16
forum: Desktop Environments
---

### Post by Rouge6 on 2012-02-16
ok heres the issue I renamed other to admin, that worked fine. Tried moving other/admin to "beside" places and had to ""kill gnome-panel" in terminal

ok...I attempted restarting..


with no luck the bottom gnome panel is there.. the main.. top isnt..

ok no biggy..

 I ctrl+Alt+T then sudo gnome-panel

gnome-panel works but..... only in root.. and I don't know how to drop root to get it to run when it boots... heres the error when I run it as sudo
-------------------------------------------------------------------------------------------------

~$ sudo gnome-panel
[sudo] password for tarvid: 

** (gnome-panel:2370): WARNING **: Could not ask session manager if shut down is available: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gnome-panel:2370): WARNING **: Could not get presence from session manager.

(gnome-panel:2370): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x9752c68'

** (gnome-panel:2370): WARNING **: Failed to get pixmap 54526036, 953, 0

** (gnome-panel:2370): WARNING **: Failed to get pixmap 54526036, 1136, 0

** (gnome-panel:2370): WARNING **: Failed to get pixmap 54525994, 1243, 0

---

### Post by Rouge6 on 2012-02-16
bump... please and thanks. I need to mention that even though bumping this soon is poor usage... that this is a laptop I use for work.>.<" and isn't mine lol

---

### Post by Rouge6 on 2012-02-16
this is what happens when I use normal user without sudo for gnome-panel command   ** (gnome-panel:2312): WARNING **: Failed to get pixmap 54525974, 1243, 0

---

### Post by Rouge6 on 2012-02-16
anyone... please?

---

### Post by Copper Bezel on 2012-02-17
Could you clarify your problem a bit, and what you were trying to do? What do you mean when you say that you "renamed other to admin"?

---

### Post by cortman on 2012-02-17
> **Rouge6 said:**
> this is what happens when I use normal user without sudo for gnome-panel command   ** (gnome-panel:2312): WARNING **: Failed to get pixmap 54525974, 1243, 0

This is a harmless bug. It's not affecting performance or accessibility, so you can safely ignore it.

@OP, I don't understand your question, so I'll offer a different solution: XFCE. Gnome2 is dying; Gnome-fallback is simply a temporary stopgap. If you want to keep a classic style desktop, go XFCE.

---

### Post by Rouge6 on 2012-02-17
true fallback is a short stop but still, the top bar doesn't load unless sudo'ed

---

### Post by Copper Bezel on 2012-02-17
Yeah, and it's a very bad idea to be running the panel as root. (Especially with sudo rather than gksu, which might itself have caused this problem by changing the permissions on a config file somewhere.) If you would, please explain what you mean to say you did here:

> ok heres the issue I renamed other to admin, that worked fine. Tried moving other/admin to "beside" places

I can't follow this. What "other," where?

---

### Post by linfidel on 2012-02-18
Perhaps he means the menu (or submenu, perhaps) called "other".  Then he tried to move this menu from the normal location in apps to a top level menu along with places.  This is, unfortunately, not possible as far as I know.

I wouldn't think renaming this menu will break anything, except that when you install a program, I think it looks for certain menus in order to add its entry. I have no idea what may have happened in trying to move it.

All I can say is, perhaps you can simply recreate it by starting with the bottom panel, adding a new panel to the top, and adding back everything like the menu, the indicators, etc.  You might want to edit the menus - try running alacarte, which is the menu editor, and see if you can fix it back to what it was.

That said, I think the comments about simply switching to xfce sucks.  I've tried it a number of times, and I personally don't think it really compares for me, anyway.  There are too many missing pieces, and the only way I would consider using it is to add in compiz, and half of Gnome - this is not particularly easy to do.  I think there are better options.  If Gnome classic is going to go away without anything to replace it, I would find it easier and better to change unity than switch to xfce.  

There's an addin called ClassicMenu indicator that lives on the top panel, and shows the classic Gnome Menu, which may help a lot of people who don't like the Unity panel.  I personally like AWN, and I like the Cardapio menu a lot (hopefully, this will live on).

xfce is not a very good answer, except perhaps for Torvalds, who has a much different set of criteria than most people, and is a little more opinionated than most.  :)

---

