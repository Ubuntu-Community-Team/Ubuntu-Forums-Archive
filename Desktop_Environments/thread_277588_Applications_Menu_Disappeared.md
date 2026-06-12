---
title: "Applications Menu Disappeared"
date: 2006-10-14
forum: Desktop Environments
---

### Post by Mazin on 2006-10-14
I'm running Xgl with Beryl, and it may be because of it that my Gnome Env's Applications menu has disappeared.  It did work after I installed Beryl, but now it's gone.

Look at the screenshot:
[IMG]http://files.aztekera.com/images/appmenu.png[/IMG]

Notice how it's only that menu that's gone.  I can still mouseover and expand the submenus, as well as activate stuff, and the Places and System menu works normally.

Help?

---

### Post by dmr_2004 on 2007-03-07
I just had the same problem and hardly could find the answer. After a lot of googling this post [http://gnomesupport.org/forums/viewtopic.php?t=11771]("http://gnomesupport.org/forums/viewtopic.php?t=11771") helped me.

In short you have to delete the following file

/.config/menus/applications.menu 

in your home directory (e.g.:  /home/yourusername//.config/menus/applications.menu )

---

### Post by 7san on 2007-03-31
Hi there everyone,

As i was reading these replies and trying to find solutions with same problem, i figured out a solution.

If your applications menu, places menu or system menu disappears in ubuntu, it is easy for you to do this:

[LIST]
[*]Hit the road to right-click the status panel
[*]choose add panel from pop-up menu
[*]Add to panel window will appear with all menus listed in categories
[*]Locate launcher & menus category
[*]then choose, menu bar and click Add button
[*]Done!!!
[/LIST]

I hope this helps others view this and old messages.

Regards,
7san

---

