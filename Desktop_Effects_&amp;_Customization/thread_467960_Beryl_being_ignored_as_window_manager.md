---
title: "Beryl: being ignored as window manager"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by Tax on 2007-06-08
I have beryl installed and running with ATi on an XGL session. However I am only able to get compiz to work as my window manager. 

If I right click on my beryl Icon and change the window manager to beryl, my previous window manager remains and does not switch over to beryl. As a result, all beryl manager settings are being ignored. Emerald will run as my window decorator, however my window borders are missing.

---

### Post by Soybean on 2007-06-08
Huh, weird... I've broken Beryl a lot of different ways, but I've never seen that one. ;) I'd recommend closing beryl-manager and running it from a terminal window, so you can watch for error output.

---

### Post by Tax on 2007-06-08
Looks like my beryl is in quite a mess. I'm amazed it runs at all right now.

Starting beryl manager with compiz as my window manager yields the following:
```

inotify_add_watch: No such file or directory
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :1.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

After which my window manager reverts to metacity.(compiz remains the selected option in the right click menu)

When I try to set beryl as my window manager I get;

```
** (beryl-manager:5578): CRITICAL **: can't execute beryl-xgl: Success
```

ad infinitum, until I change back to metacity or compiz.

---

### Post by Soybean on 2007-06-08
Well, that's pretty cryptic. I especially like that second error message. I mean, "Success"? Success with what? Not executing beryl-xgl, apparently. ;)

Those first errors sound like compiz is having some sort of trouble... maybe try disabling it first? I haven't heard of any conflicts between the two, but I can imagine it happening.

Other than that, I'm a little lost. Hopefully someone with more ATI/XGL experience has some insight. :confused:

---

### Post by ykpaiha on 2007-06-08
beryl as wm ?
compiz wm ?

<NO NO NO>

I guess you have a bad explaination somewhere...
to run beryl you need:
xorg => i hope you have it
then a window manager => gnome, kde, xfce etc...
the right driver ati or nvidia or else well configured
when and only when these are running you can load one of them beryl or and i say or !!! compiz....(after insttalling it of course)
then and only then you will be able (with beryl mainly) or will have the oppotunity to change the decorator or else...

---

### Post by Soybean on 2007-06-09
I'm pretty sure he had the correct terminology, ykpaiha.

If you right-click on your beryl-manager icon, there's a spot to "select window manager." Options there are beryl, metacity, compiz (if installed), etc. Those are window managers. Gnome, KDE, XFCE are "desktop environments." As for window decorators, that would be things like Emerald, Heliodor, Aquamarine, etc.

And he has both Beryl and Compiz installed, and Compiz is working, so it seems fairly safe to assume that he's got Xorg, a desktop environment, and appropriate video drivers.

---

