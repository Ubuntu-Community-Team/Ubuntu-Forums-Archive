---
title: "Splash Screen during startup?"
date: 2005-07-19
forum: Desktop Environments
---

### Post by brian.reading on 2005-07-19
I think the Ubuntu default GUI is pretty polished, and is one of the best out of any *nix installation I've done.  However, I've always wondered, is it possible to have some sort os splash screen with a progress bar instead of having a text startup? OS X has one, and so does Windows XP.  To me, it feels like the mark of a good GUI.

So what's the verdict?

---

### Post by codejunkie on 2005-07-19
[QUOTE=brian.reading]I think the Ubuntu default GUI is pretty polished, and is one of the best out of any *nix installation I've done.  However, I've always wondered, is it possible to have some sort os splash screen with a progress bar instead of having a text startup? OS X has one, and so does Windows XP.  To me, it feels like the mark of a good GUI.

So what's the verdict?[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=41709&highlight=splashy](http://ubuntuforums.org/showthread.php?t=41709&highlight=splashy) this might be what your looking for i think there including bootsplash in the next release hope this helps.

---

### Post by brian.reading on 2005-07-19
[QUOTE=codejunkie][http://ubuntuforums.org/showthread.php?t=41709&highlight=splashy](http://ubuntuforums.org/showthread.php?t=41709&highlight=splashy) this might be what your looking for i think there including bootsplash in the next release hope this helps.[/QUOTE]
That's exactly what I'm looking for! Thanks a lot!

---

### Post by phubai on 2005-07-19
You sure can...google Splash Screen and you should come up with something you'd like, then add it to your /boot/grub/menu.lst like this:

```
# splash image
splashimage=(hd0,4)/boot/grub/images/gentoo.xpm.gz
```

In this example, I am using splash image gentoo.xpm.gz that I have copied to the directory shown (/boot/grub/images/). As with any grub configuration, make sure you have your drive and partition correct.

It's a very good idea to copy your menu.lst to the same directory naming it menu.lst.old or something like that. If you have a problem (and sometimes graphics can cause them on startup), you can always revert back to the original menu.lst.

pb

---

