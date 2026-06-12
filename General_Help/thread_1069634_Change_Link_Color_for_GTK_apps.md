---
title: "Change Link Color for GTK apps?"
date: 2009-02-14
forum: General Help
---

### Post by GrammatonCleric on 2009-02-14
I'm looking for a way to change the default blue gtk link color to something that works better with darker themes.  I've done a little research and it appears that adding something like...

```

[GtkWidget]("https://wiki.ubuntu.com/GtkWidget")::link-color=@fg_color
[GtkWidget]("https://wiki.ubuntu.com/GtkWidget")::visited-link-color = shade

```...to a theme's gtkrc will resolve this but I'm not quite sure how to use these or where to place them with in the gtkrc theme file.  

Thanks,
- GC

---

### Post by sirjoebob on 2009-02-14
You could probably just use Gnome color chooser. It is available in the repositories and allows a pretty simple, graphical way to manage most of the color decisions for a system.

---

### Post by GrammatonCleric on 2009-02-14
got it installed but after more than several trial and error attempts can't seem to find where the link color is in gnome-color-choose.  Any pointers?

Thanks,
-GC

---

### Post by GrammatonCleric on 2009-02-14
Here's an example of what I'm trying to change.  The screen shot below is of Evolution with a dark theme.  The highlighted areas in red are of the blue url and links that are of the default gtk blue.

---

### Post by sirjoebob on 2009-02-14
I am not positive on how to do it, just thought it may help. I would say it is the first section of options. If not, maybe someone else will come to the rescue on this one.... lol

---

### Post by JackTheDipper on 2009-02-16
You can find this option on the tab "specific": [http://gnomecc.sourceforge.net/assets/galleries/49/1screenshot3.png](http://gnomecc.sourceforge.net/assets/galleries/49/1screenshot3.png)

(available since GNOME Color Chooser 0.2.4)

Good luck! ;-)

---

