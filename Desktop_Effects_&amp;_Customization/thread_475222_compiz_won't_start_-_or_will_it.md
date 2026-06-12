---
title: "compiz won't start - or will it?"
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by Thorndeux on 2007-06-15
I upgraded to compiz 0.5 and it won't start or I'm not starting it properly.

This is what I did and what it says:

```
thorn@ubunthorn:~$ compiz --replace gconf &
[1] 10875
thorn@ubunthorn:~$ /usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'keybinding'
/usr/bin/compiz: line 475: 10940 Segmentation fault      (core dumped) ! ( $COMPIZ $ARGS $PLUGINS >> $OUTPUT 2>> $OUTPUT )
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

Are packages missing or something? All I did was adding repositories to the package sources and the Update Manager updated compiz for me.

---

### Post by Thorndeux on 2007-06-15
It seems that compiz is running in the background, but metacity is still the active windows manager (that's what the System Monitor tells me).
So I guess that metacity is not replaced because compiz is not properly started? ARGHH!?

---

### Post by Thorndeux on 2007-06-15
I reversed to the original Ubuntu version of compiz and it works fine now.

---

