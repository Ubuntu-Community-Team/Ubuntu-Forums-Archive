---
title: "QGtkStyle + 64-bit (forced) skype?"
date: 2008-11-08
forum: Desktop Environments
---

### Post by macaholic on 2008-11-08
I had recently discovered [QGtkStyle]("http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/") , and have been using it with much success with all of y qt4 apps. However, skype will not comply, even after running it with --disable-cleanlooks -style GTK. I suspect this has to do with skype being forced to run in a 64-bit environment and the qt themes not being compatible, or something along those lines. In any case, does anyone have a suggestion as to a possible fix for this problem? Or is this just a matter of having a native skype in 64-bit linux? (which in and of itself is a ridiculous topic, how can they NOT have one? It can't possibly be that hard. I know they have low staff, but I can't see any large technical obstacles preventing them from making one.)

---

### Post by macaholic on 2008-11-10
My one and only bump

---

### Post by MasterProg on 2008-12-29
The problem is that 32 bit Skype can't use 64 bit QGtkStyle. You have to install a 32 bit version of this style (get it [here]("http://ubuntuforums.org/showthread.php?t=834784")) to make it work with Skype. Download deb file, extract is as /usr/lib/qt4/plugins/styles/libgtkstyle32.so or whatever you like.

Hope this helps.

---

### Post by macaholic on 2008-12-31
Sweet thanks, wasn't expecting a reply from such an old thread. I didn't think of copying the .so file.

---

