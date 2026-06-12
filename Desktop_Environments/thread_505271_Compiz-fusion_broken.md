---
title: "Compiz-fusion broken"
date: 2007-07-20
forum: Desktop Environments
---

### Post by Hayesio on 2007-07-20
Hi everyone

I installed compiz-fusion a couple of weeks back and it was working perfectly.  Then I got some auto-updates and they broke compiz-fusion - it said something about not being able to load ccp plugin because of ABI mismatch.  I did some looking around and found people with similar problems and the advice given was to change the repository from tuxfamily to vorian and then update compiz-fusion.  I did this but its still not working.

The new terminal output reads:

```
 /usr/bin/compiz: line 475:  8062 Segmentation fault      (core dumped) ! ( $COMPIZ $ARGS $PLUGINS >> $OUTPUT 2>> $OUTPUT )
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "murrine",
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed

```

Does anyone know how I can fix this?

thanx

---

### Post by catanzag on 2007-07-20
I't a (more o less common) problem due to a not fully alignment of all libraries; sometimes randomly I got it too and I solved, with a further update some time later; I know it's a bit annoying, but I think that we can bear this as, in this phase, it is still in the development phase.

You could also check [this thread]("http://ubuntuforums.org/showthread.php?t=495549").

regards

catanzag

---

### Post by catanzag on 2007-07-21
Today I got again the same error (though not after *apt-get update*, so pkgs could be a bit older); what I noticed is that ccp plugin is contained in *libcompizconfig0* package, which is not automatically installed after *compizconfig-settings-manager* or *libcompizconfig-backend-*,*, so one solution could be the manual selection of this package for installing.

---

### Post by Hayesio on 2007-07-23
Ok, I've got my problem down to this:

```


jack@Star-Ship-Omega:~$ compiz --replace
/usr/bin/compiz: line 475:  9654 Segmentation fault      (core dumped) ! ( $COMPIZ $ARGS $PLUGINS >> $OUTPUT 2>> $OUTPUT )


```

I installed gtk2-engine-murrine.

Any Idea's?

Thanx

---

