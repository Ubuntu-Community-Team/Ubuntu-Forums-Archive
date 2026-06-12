---
title: "How do I make window draging non-opaque"
date: 2005-05-23
forum: Desktop Environments
---

### Post by parktownprawn on 2005-05-23
How do I make window draging non-opaque with gnome and metacity?

In other words when I move a window around it doesn't redraw the window (and eat up lots of cpu) but just gives me an outline until i drop the window. 

i looked around the gconf-editor options but couldn't find anything

---

### Post by matej on 2005-05-23
You can try this:
[http://www.gnome.org/learn/admin-guide/2.2/ch07s02.html#performance-5](http://www.gnome.org/learn/admin-guide/2.2/ch07s02.html#performance-5)
But it doesn't work for me :-(

---

### Post by parktownprawn on 2005-05-23
thanks for the tip but it doesn't work for me either :(

---

### Post by matej on 2005-05-23
I got it:
```
gconftool-2 --type bool --set /apps/metacity/general/reduced_resources true
``` 
and you probably must have accessibility (menu system -  settings -  Assistive Technology) disabled.

It's grate when you have sources :)
metacity-2.10.0/src/display.c:
 ```
display->grab_wireframe_active =
	    (meta_prefs_get_reduced_resources () && !meta_prefs_get_gnome_accessibility ())  && 
		(meta_grab_op_is_resizing (display->grab_op) ||
		 meta_grab_op_is_moving (display->grab_op));

```

---

### Post by parktownprawn on 2005-05-24
Great that works - thanks alot.

Initially it didn't work because I typed the comand as root

```
sudo gconftool-2 --type bool --set /apps/metacity/general/reduce d_resources true
```
 
which much have set the global preferences but not my local user preferences.

after simply typing issuing the command without sudo it worked.

I guess i was misled by the # before the commands at
 
[http://www.gnome.org/learn/admin-gu...l#performance-5](http://www.gnome.org/learn/admin-gu...l#performance-5)   

which made me think i had to do everything as root.

---

