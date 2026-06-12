---
title: "Windows won't &quot;opacify&quot; when moving"
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by dmber on 2007-10-16
I have the Move Windows plugin "Opacity" set to 50.  Moving the windows does not make them transparent though.

I used to have it set to where I could grab a Window Bar it would go transparent.  I miss that...

What could I have set that would be conflicting with this?

---

### Post by Rupertronco on 2007-10-16
Do you have the opacify plugin enabled? It's in the Accesibility tab.

---

### Post by dmber on 2007-10-16
yup.  when i move my cursor over a non-focused window, the focused window will go transparent after a delay.

---

### Post by Rupertronco on 2007-10-16
Turn that off to see if it's the one messing with the opacity on drag.

---

### Post by dmber on 2007-10-17
that's what's messing it up.  is there any way i can have them both running at the same time?  i like opacify...

---

### Post by Rupertronco on 2007-10-17
Not sure, I never use the opacify plugin. However, on my version of compiz (latest git build) they are not conflicting. I think your only option in this case is to update your compiz install. which are you using?

---

### Post by dmber on 2007-10-17
umm...how do i find out which version i'm running?

---

### Post by Rupertronco on 2007-10-17
```
dpkg -l | grep compiz*
```

---

### Post by dmber on 2007-10-17
```
ii  belocs-locales-bin                         2.4-2ubuntu2                           tools for compiling locale data files
ii  compiz                                     0.5.2+git20070918-0ubuntu5~ppa1        OpenGL window and compositing manager
ii  compiz-core                                0.5.2+git20070918-0ubuntu5~ppa1        OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070917-0ubuntu1~ppa1        Collection of extra plugins from OpenCompositing for C
ii  compiz-fusion-plugins-main                 0.5.2+git20070917-0ubuntu3~ppa1        Collection of plugins from OpenCompositing for Compiz
ii  compiz-gnome                               0.5.2+git20070918-0ubuntu5~ppa1        OpenGL window and compositing manager - GNOME window d
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk window dec
ii  compiz-plugins                             0.5.2+git20070918-0ubuntu5~ppa1        OpenGL window and compositing manager - plugins
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1~ppa1          Decorator for compiz-fusion
ii  g++                                        4.1.2-1ubuntu1                         The GNU C++ compiler
ii  g++-4.1                                    4.1.2-0ubuntu4                         The GNU C++ compiler
ii  gcc                                        4.1.2-1ubuntu1                         The GNU C compiler
ii  gcc-4.1                                    4.1.2-0ubuntu4                         The GNU C compiler
ii  libcompizconfig-backend-gconf              0.5.2+git20070918-0ubuntu1~ppa1        Settings library for plugins - OpenCompositing Project
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2~ppa1        Settings library for plugins - OpenCompositing Project
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1          Decoration engines for compiz-fusion
ii  mono-jit                                   1.2.3.1-1ubuntu1                       fast CLI JIT/AOT compiler for Mono
ii  pkg-config                                 0.21-1build1                           manage compile and link flags for libraries
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings
```

---

### Post by Rupertronco on 2007-10-17
I guess your best bet at this point is to use trevino's repo and update to the newest version (I have that installed on my laptop without any conflict between the aformentioned plug-ins)

---

### Post by Forlong on 2007-10-18
Gutsy's packages don't have any conflicts as well. :)

---

### Post by Rupertronco on 2007-10-18
> **Forlong said:**
> Gutsy's packages don't have any conflicts as well. :)

Even better. You could go for the twofer and upgrade to gutsy as well!

---

### Post by dmber on 2007-10-18
i'm about to!

thanks for the help!  i have routed a couple buddies to your How To: CF, Forlong.

---

### Post by dmber on 2007-10-19
ok, i upgraded to gutsy last night.  all my settings and whatnot made it through the upgrade, but opacify and move window still conflict.  i don't think i'm using the right version of Compiz-Fusion.

Is there a guide for getting rid of the CF  I have now and getting the one that's right for Gutsy?

---

### Post by dmber on 2007-10-19
> **Forlong said:**
> Gutsy's packages don't have any conflicts as well. :)
so it Gutsy seems to have kept my old packages because I still have the conflict.  Should I uninstall CF and start over or something?  I'm starting to wish I had just re-installed with Gutsy instead of upgrading...

---

### Post by Forlong on 2007-10-19
See here: [http://ubuntuforums.org/showthread.php?t=580063](http://ubuntuforums.org/showthread.php?t=580063)

---

### Post by Rupertronco on 2007-10-19
In my opinion you should back up your home directory and do a fresh install. The upgrade install isn't exactly what I'd call bug free. I think the best method would certainly be just to wipe your feisty install and start from scratch.

---

### Post by dmber on 2007-10-21
i did a fresh install.  

everything works great.  thanks for checking back on my progress.  i appreciate it.

---

