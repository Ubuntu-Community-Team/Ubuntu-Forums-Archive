---
title: "[SOLVED] GTK2+ theme &amp;quot;imetal-gradient-macmenu&amp;quot; is not installed"
date: 2008-12-15
forum: General Help
---

### Post by Sultan-mrm on 2008-12-15
Hi all,

I found imetalv6 theme here:

[http://gnome-look.org/content/show.php/imetalV6?content=77057](http://gnome-look.org/content/show.php/imetalV6?content=77057)

when I drag and drop in theme aria it gave me this message

[[img]http://www.mrkzy.com/uploads/b20cf1e0414c.jpg[/img]](http://www.mrkzy.com/download.php?filename=b20cf1e0414c.jpg)

and I google it to find how install it but no luck .

can you tell me how to install it on ubuntu 8.10.

Best Regards,



sultan

---

### Post by Ivo Moelans on 2008-12-16
In */home/<username>/.themes/imetalV6i* is a file called *index.theme*. This file 'tells' the theme which components to load. In this theme it is a bit of a mess.
Open it with Text Editor with superuser privileges (terminal: *sudo gedit*) and copy and paste this code in it:

```
[Desktop Entry]
Name=imetalV6i
Comment=imetal port for gtk
Encoding=UTF-8
Type=X-GNOME-Metatheme

[X-GNOME-Metatheme]
GtkTheme=imetalV6i
MetacityTheme=Human
IconTheme=Human
CursorTheme=default
CursorSize=18
```

MetacityTheme: imetalV6i doesn't come with its own Metacity theme, but you can define any Metacity theme that is installed on your system.
IconTheme: basically the same. The theme will load any icon theme (present on your system) you define here.
CursorTheme: also the same.
After applying this code in the *index.theme* file, in Nautilus it will rename itself to *imetalV6i*.

Hope this helps.

---

### Post by Sultan-mrm on 2008-12-16
> **Ivo Moelans said:**
> In */home/<username>/.themes/imetalV6i* is a file called *index.theme*. This file 'tells' the theme which components to load. In this theme it is a bit of a mess.
Open it with Text Editor with superuser privileges (terminal: *sudo gedit*) and copy and paste this code in it:

```
[Desktop Entry]
Name=imetalV6i
Comment=imetal port for gtk
Encoding=UTF-8
Type=X-GNOME-Metatheme

[X-GNOME-Metatheme]
GtkTheme=imetalV6i
MetacityTheme=Human
IconTheme=Human
CursorTheme=default
CursorSize=18
```

MetacityTheme: imetalV6i doesn't come with its own Metacity theme, but you can define any Metacity theme that is installed on your system.
IconTheme: basically the same. The theme will load any icon theme (present on your system) you define here.
CursorTheme: also the same.
After applying this code in the *index.theme* file, in Nautilus it will rename itself to *imetalV6i*.

Hope this helps.




:guitar::guitar::guitar:


Great,

It's works.....


Explanation is useful, and thanks for effort

---

