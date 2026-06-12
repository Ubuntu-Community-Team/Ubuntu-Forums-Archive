---
title: "Help editing theme - GTKrc File"
date: 2009-04-25
forum: General Help
---

### Post by Devi 710 on 2009-04-25
I love the GTK 2 theme 'Grace' found here:
[http://www.gnome-look.org/content/show.php/GRACE?content=101070](http://www.gnome-look.org/content/show.php/GRACE?content=101070)

The only thing I want to change is that **the main menu is too large**. It looks great in the preview on gnome-look, but mine is too fat. The author made it with the global-menu app in mind, so that may be the reason.

The lines:
&#65279;
> # icon sizes
 #gtk-icon-sizes = "gtk-menu=16,16:\ngtk-button=16,16:\ngtk-dnd=16,16:\npanel-menu=16,16:\npanel=16,16:\ngtk-dialog=16,16:"

actually look correct. 16 should be the proper size, but my main menu looks more like 28 or 32 or something.

I've tried removing the "#", removing the 'n' before 'npanel', and changing the numbers to something smaller like 12. Logged in and out, but no luck.

What do I need to do?

Thanks,

Devi

---

### Post by Devi 710 on 2009-04-25
Just a quick bump. :)

It's busy these days with the new release out.

---

### Post by Devi 710 on 2009-04-25
I found the information I needed here:

[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

Plus a little experimenting and looking at another gtkrc file. I added the line:

gtk-icon-sizes = "panel-menu=20,20"

and got the look I desired. I found out that "commenting" or lines that begin with '#' are canceled out.

---

