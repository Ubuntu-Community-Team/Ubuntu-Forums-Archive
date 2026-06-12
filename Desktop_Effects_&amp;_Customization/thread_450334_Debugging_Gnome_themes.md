---
title: "Debugging Gnome themes"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by NilsE on 2007-05-21
I have thought often about how to debug GTK-2.0 themes (currently under Feisty 7.04) but never took the time to look for a tool.  However, over the weekend I accidentally found a way to do minor debugging.  

If you go into a terminal and run 

```
gksudo gedit

If there is nothing wrong with the theme you will get the normal 
(known bug) error message:

nils@Nils-laptop:~$ gksudo gedit
(gedit:6777): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and 
host-based authentication failed.
nils@Nils-laptop:~$
```

```
gksudo gedit

If there is an error in the theme such as a missing file you will not get the normal error message but 
will have other information in it such as:

nils@Nils-laptop:~$ gksudo gedit
/usr/share/themes/Silver/gtk-2.0/gtkrc:338: Unable to locate image file in pixmap_path: "MenuPattern.png"
/usr/share/themes/Silver/gtk-2.0/gtkrc:342: Background image options specified without filename
nils@Nils-laptop:~$ 
```

If this has already been noted this post can be deleted.

---

