---
title: "Downgrade compiz-fusion?"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by Hawk__0 on 2007-12-03
Is it possible for me to downgrade compiz-fusion?
I have the newest version... if i type compiz --version it shows version 0.6.3, but i get this if i do dpkg -l | grep compiz:
```

steve@steve:/media/cdrom0$ dpkg -l | grep compiz
ii  compiz-bcop                                0.6.100~git20070906+3v1ubuntu0       Compiz option code generator
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager
ii  compiz-dev                                 1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1    Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20

```

I want to downgrade to... i think its 0.6.0 or 0.6.2, whichever is default installed with gutsy, because I want the extra plugins.

Can I do this??

---

### Post by Hawk__0 on 2007-12-03
bump

---

### Post by ronmarley1 on 2007-12-04
How did you install the updated git version?  If you added a third party repository and used apt or Synaptic, what I would do first is to uninstall all files related to compiz.  Then, comment out the repository you used to get the updated version.  Reload your repos and reinstall compiz, and that should be the default version with Gutsy.

I have compiz 0.6.1, which I think is the default with Gutsy.

---

