---
title: "java RE and human theme"
date: 2006-03-19
forum: Desktop Environments
---

### Post by Manuka on 2006-03-19
Hi all,

I have a similar problem to the one posted there:
[http://www.ubuntuforums.org/showthread.php?t=52113&highlight=java+human](http://www.ubuntuforums.org/showthread.php?t=52113&highlight=java+human)

In a few words, I am trying to run a program using java from the Terminal. I am using sun JRE 1.5 update 6, and I made it my default java using
```
update-alternatives --config java
```

IUnfortunately, trying two different programs, I receive this error message:
```
/usr/share/themes/Human/gtk-2.0/gtkrc:7: Failed to parse property value " GTK_SHADOW_NONE " for `GtkMenuItem::shadow-type'
/usr/share/themes/Human/gtk-2.0/gtkrc:58: Engine "clearlooks" is unsupported, ignoring
Uncaught error fetching image:
java.lang.NullPointerException
        at sun.awt.image.URLImageSource.getConnection(Unknown Source)
        at sun.awt.image.URLImageSource.getDecoder(Unknown Source)
        at sun.awt.image.InputStreamImageSource.doFetch(Unknown Source)
        at sun.awt.image.ImageFetcher.fetchloop(Unknown Source)
        at sun.awt.image.ImageFetcher.run(Unknown Source)
```

Any help would be as welcome as heaven! The trick proposed in the link above did not have any affect on the outcome...

Thanks!!!

Manu

---

### Post by Manuka on 2006-03-21
any more ideas???

pleaaaase someone

---

