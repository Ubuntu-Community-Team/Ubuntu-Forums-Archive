---
title: "GTK themes in KDE"
date: 2011-07-28
forum: Desktop Environments
---

### Post by Antonio_M on 2011-07-28
Hello!
I have a problem with a GTK themes in KDE environment.
When I set the GTK style in application's styles in control center, it's looks like this screen:

[ATTACH]198674[/ATTACH]

Arrows on "places" and "files": In GTK it's a "GtkTreeView" widget class and I can't separate they. It's only one color for a two things, cause it's the GtkTreeView.
But I need to have different colors for the places and files.

How I can get what I want?
GTK theme: Atolm [http://gnome-look.org/content/show.php/Atolm?content=136789](http://gnome-look.org/content/show.php/Atolm?content=136789)
KDE 4.6.4

~/.gtkrc-2.0-kde4:

```
    include "/usr/share/themes/Atolm/gtk-2.0/gtkrc"
    style "user-font"
    {
       font_name="Droid Sans"
    }
    widget_class "*" style "user-font"
    gtk-theme-name = "Atolm"
```

---

