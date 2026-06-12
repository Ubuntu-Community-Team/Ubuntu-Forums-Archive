---
title: "need key bindings to show up in ccsm"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by sdowney717 on 2007-12-28
can anyone tell me why my system's ccsm does not show the keybindings for the plugins?
ATI video card with gutsy installed. I tried uninstalling compiz completely and reinstalling but ccsm never shows me the keybindings. Just imagine you go into ccsm and look at the plugins and there are no keybindings listed that tell you how to make any othem work.

The synaptic shows exactly the same items installed when searching for compiz on another working gutsy computer.

My other gutsy computer with nvidia shows the keybindings list in ccsm for each plugin.

---

### Post by ajmorris on 2007-12-28
so there are no keybindings for **any** of the plugins? strange, what version of compiz are you running?

---

### Post by Forlong on 2007-12-28
Yeah that's weird. Did you install any third party packages?

Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by sdowney717 on 2007-12-28
scott@scott-desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager
rc  compiz-extra                               0.3.6.1-0ubuntu2                          extra third party plugins for compiz
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1                Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2                Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                         OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1                  Decorator for compiz-fusion
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1                Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1                  Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings

---

### Post by sdowney717 on 2007-12-28
for example the negative plugin
should be ctrl plus m etc with a keybinding header

---

### Post by sdowney717 on 2007-12-28
and these 2 plugins here.

as far as I know, I am not using 3rd party repos.

---

### Post by sdowney717 on 2007-12-28
how are you all starting ccsm?
I either type it in terminal or goto menu system-preferences-compizconfig settings manager

I do believe the other working gutsy system did not have this in the menu, it was called something like desktop settings yada etc...
so that is the only diff I remember. 
I dont have access to the other comp now as we were visiting my parents. BUT I did notice his gutsy had key bindings listed in ccsm and mine did not. So I know something is not right in my system.

---

### Post by Forlong on 2007-12-28
Could you please repost the output using the CODE tags please.

Click on "Post Reply" and hit the # button to use them.


And please use the EDIT function instead of posting several times.

---

### Post by sdowney717 on 2007-12-28
```

scott@scott-desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager
rc  compiz-extra                               0.3.6.1-0ubuntu2                          extra third party plugins for compiz
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1                Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2                Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                         OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1                  Decorator for compiz-fusion
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1                Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1                  Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings



```

---

### Post by 0g_Trans_Fat on 2007-12-28
I am having the same problem, and here is my output
```
ii  compiz                                     1:0.6.3+git20071205+Qubuntu0              OpenGL window and compositing manager
ii  compiz-bcop                                0.5.2-0ubuntu1                            Compiz option code generator
ii  compiz-core                                1:0.6.3+git20071205+Qubuntu0              OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.6.99+git20071121+Qubuntu0               Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.6.99+git20071121+Qubuntu0               Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-unsupported          0.6.99+git20071121+Qubuntu0               Collection of plugins for Compiz - Unsupport
ii  compiz-gnome                               1:0.6.3+git20071205+Qubuntu0              OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                         OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.3+git20071205+Qubuntu0              OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
rc  gnome-compiz-manager                       0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  libcompizconfig0                           0.6.99+git20071127+Qubuntu0               Settings library for plugins - Compiz Fusion
rc  libgnome-compiz-manager0                   0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  python-compizconfig                        0.6.99+git20071106+Qubuntu0               Python bindings for the Compiz Configuration

```

I asked about this on the Compiz-Fusion forums, and this is the response i got, however i am not sure what it means.

> My problem was that I had an older version of the ccsm program (binary) from an earlier installation that should have been removed when I had upgraded but was still on my system and was being executed instead of the correct one (because of how the paths were searched) - i.e. the ccsm program that I was running was not the one that matched the libcompizconfig libary thus things were out of sync.

You should check that your .deb's are matched (in Suse they would include: compizconfig-settings-manager and libcompizconfig and python-compizconfig) and that the one being executed (in a konsole type "which ccsm") is the correct one


You could also try renaming your compiz config folder(might be ~/.config/compiz) to see if that got corrupted and is causing the problem

---

### Post by sdowney717 on 2007-12-28
compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1

I did a complete uninstall in synaptic and reinstall and it made no difference.
I would think an uninstall and then reinstall would put the right binary into the path.
the folders beginning with '.' are hidden.

[http://packages.ubuntu.com/gutsy/x11/compizconfig-settings-manager](http://packages.ubuntu.com/gutsy/x11/compizconfig-settings-manager)
google search found this and I assume it is current version.
Any truth that the path is running some old decrepit ccsm version, even though listing out compiz does not show this to be true?

---

### Post by Forlong on 2007-12-28
sdowney717, please remove these:
```
sudo apt-get remove --purge gnome-compiz-manager libgnome-compiz-manager0
```
As well as these old config files:
```
sudo dpkg --purge compiz-extra compiz-gtk
```
Let's see if it helps.


0g_Trans_Fat, where did you get your packages?

---

### Post by sdowney717 on 2007-12-28
did this and still no key bindings are shown.
My history with this box is I upgraded to gutsy from feisty on the release day.
And I used to use trevino's repositories with Feisty, but not anymore with Gutsy.


thanks for the help so far.
Is there a way to tell if the right versions for compiz-fusion are starting?

---

