---
title: "Couldn't load ccp"
date: 2007-09-21
forum: Desktop Effects &amp; Customization
---

### Post by Decline- on 2007-09-21
Hi there,

I am running an XGL session with an ATI graphics card and fglrx. Compiz Fusion has worked before... 

Well the problem is, when I installed Compiz Fusion (have tried both Amaranth, Trevi&#324;o and Vorians repo) and launch it from fusion-icon (or manually) I get this: 

 ... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp
compiz (core) - Error: Couldn't load plugin 'ccp'

And I get this error with every repo!

Here's the installed files:

```
$ dpkg -l | grep compizii  compiz                                     0.5.5~git20070917+3v1ubuntu1               OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070917+3v1ubuntu1               OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20070917+3v1ubuntu1               Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20070917+3v1ubuntu1               Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070917+3v1ubuntu0               Collection of UNOFFICIAL fusion plugins for 
ii  compiz-gnome                               0.5.5~git20070917+3v1ubuntu1               OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                            OpenGL window and compositing manager - Gtk 
rc  compiz-kde                                 0.5.5~git20070917+3v1ubuntu1               OpenGL window and compositing manager - KDE 
ii  compiz-plugins                             0.5.5~git20070917+3v1ubuntu1               OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20070917+3v1ubuntu1              Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.5.2~git20070909+3v1ubuntu0               GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2~git20070909+3v1ubuntu2               Settings library for plugins - Compiz Fusion
ii  python-compizconfig                        0.5.2~git20070903+3v1ubuntu0               Python bindings for the Compiz Configuration

```

(The Gtk, KDE, GNOME - packages aren't really there.. not uninstallable with apt-get at least)

Any tips?

---

### Post by Decline- on 2007-09-21
Could it be compiz-gnome/gtk/KDE that has left some files behind from an earlier install?

ii compiz-gnome 0.5.5~git20070917+3v1ubuntu1 OpenGL window and compositing manager - GNOM
rc compiz-gtk 0.3.6-1ubuntu13 OpenGL window and compositing manager - Gtk
rc compiz-kde 0.5.5~git20070917+3v1ubuntu1 OpenGL window and compositing manager - KDE
ii compiz-plugins

Or could it be some python error? :

~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 39, in <module>
    from ccm.Utils import GlobalUpdater
ImportError: cannot import name GlobalUpdater

$ python --version
Python 2.5.1

---

### Post by hyperair on 2007-09-21
Do you get an ABI version error when you try to load Compiz? Because that error message you provided doesn't seem complete. Before you installed via Trevino's repository, did you install via any other method? Perhaps Vorian's or Amaranth's repository, or compiling yourself?

In any case, I suggest a complete reinstall of Compiz Fusion:
```

sudo apt-get autoremove --purge compiz*
sudo apt-get install compiz compizconfig-settings-manager compiz-fusion* libcompizconfig-backend-gconf

```

---

### Post by Decline- on 2007-09-21
Tried what you said, same error again... But yes I have tried both from Treviño, Amaranth and Vorians rep before, as well as compile from GIT. So there COULD be some files around somewhere...  tho I can't find any important files with "find compiz" after uninstalling. (just apt-archive files etc..)

---

### Post by Forlong on 2007-09-21
> **Decline- said:**
> And I get this error with every repo!
Trust me, you won't get this when properly installing the packages from Amaranth's repository.
Just make sure to remove any previous packages installed and disable all other third-party repositories.

You can use this guide if you like: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
If you have any troubles with that, please post here: [http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149) (so I will notice your post right away)

---

### Post by Decline- on 2007-09-21
Works! What I did was enter some GIT folders I had extracted and compiled some while ago, and do make uninstall. Probably some stuff was left behind since that. And then I reinstalled the Amaranth packages. Works!

---

