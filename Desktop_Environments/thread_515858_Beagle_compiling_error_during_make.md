---
title: "Beagle compiling error during make"
date: 2007-08-02
forum: Desktop Environments
---

### Post by badmadrabbit on 2007-08-02
Hello there!

I got the following error when I tried to compile the Beagle version 2.17 from source during make: 

```
In file included from /usr/include/gtk-2.0/gtk/gtkwidget.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkcontainer.h:33,
                 from /usr/include/gtk-2.0/gtk/gtksocket.h:29,
                 from /usr/include/gtk-2.0/gtk/gtkplug.h:31,
                 from eggtrayicon.h:24,
                 from eggtrayicon.c:25:
/usr/include/gtk-2.0/gtk/gtkobject.h:85: error: expected specifier-qualifier-list before 'GInitiallyUnowned'
/usr/include/gtk-2.0/gtk/gtkobject.h:97: error: expected specifier-qualifier-list before 'GInitiallyUnownedClass'
eggtrayicon.c: In function 'egg_tray_icon_update_manager_window':
eggtrayicon.c:344: error: 'GtkObject' has no member named 'flags'
make[2]: *** [eggtrayicon.lo] Fehler 1
make[2]: Verlasse Verzeichnis '/home/jona/beagle-0.2.17/glue'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/jona/beagle-0.2.17'
make: *** [all] Fehler 2

```

I have no idea what this is all about, maybe someone can help me :)

Cheers,
Jona

---

### Post by apetresc on 2007-08-04
Seems to be a library version mismatch. You could try running ```
sudo apt-get build-dep beagle
``` in order to get all the libraries Beagle needs. Though really configure should have caught that sort of problem.

But is there any particular reason you are compiling beagle from source instead of grabbing Ubuntu's package?

---

### Post by badmadrabbit on 2007-08-05
Beagle did not index the evolution data, so I though compiling it may solve the problem.

---

