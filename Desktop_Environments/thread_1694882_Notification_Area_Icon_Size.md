---
title: "Notification Area Icon Size"
date: 2011-02-25
forum: Desktop Environments
---

### Post by lpcstr on 2011-02-25
I noticed that if I set my gnome panel size to 48 px that the icons in the notification area also expand to 48 px. Is there a way to limit their size?

Here is an example of what I'm looking for. 

[http://www.linuxtopia.org/online_books/linux_beginner_books/redhat_9_getting_started_guide/figs/desktop/firstdesk.png](http://www.linuxtopia.org/online_books/linux_beginner_books/redhat_9_getting_started_guide/figs/desktop/firstdesk.png)

---

### Post by An Sanct on 2011-02-25
In Ubuntu, when I right click on a panel, select "Properties", I can set the height of the panel, which also controls the height/size of the icons.

Which distribution are you using?

---

### Post by lpcstr on 2011-02-25
> **An Sanct said:**
> In Ubuntu, when I right click on a panel, select "Properties", I can set the height of the panel, which also controls the height/size of the icons.

Which distribution are you using?

No, I want the panel and my launcher icons to be 48px, but I want my notification icons to be smaller. If you look in the image link I provided, that is exactly what you will see.

---

### Post by ve4cib on 2011-02-25
Is that picture even Gnome?  It almost looks more like an old version of KDE to me.

As far as I know what you're asking for is not possible with the current Gnome Panel.  There may be a gconf setting lurking somewhere that you can tweak, but I doubt it.

---

### Post by lpcstr on 2011-02-25
> **ve4cib said:**
> Is that picture even Gnome?  It almost looks more like an old version of KDE to me.

As far as I know what you're asking for is not possible with the current Gnome Panel.  There may be a gconf setting lurking somewhere that you can tweak, but I doubt it.

The picture is of Red Hat 9 with Gnome 2.2, so I have to believe that it can be done.

---

### Post by Krytarik on 2011-02-26
You could try to use the "gtk-icon-sizes" option in your "~/.gtkrc-2.0":
[http://www.gtk.org/api/2.6/gtk/GtkSettings.html#GtkSettings--gtk-icon-sizes](http://www.gtk.org/api/2.6/gtk/GtkSettings.html#GtkSettings--gtk-icon-sizes)

But there seems to be no specific identifier for the items in the notification area, I only found "gtk-status-icon", but those is not even mentioned to be a possible identifier for that option. Try searching in that direction.

---

### Post by lpcstr on 2011-02-27
> **Krytarik said:**
> But there seems to be no specific identifier for the items in the notification area

Well then that's not particularly helpful. I guess if you want something done right you have to do it yourself. If you need me I'll b re-writing the notification-area applet. ](*,)

---

