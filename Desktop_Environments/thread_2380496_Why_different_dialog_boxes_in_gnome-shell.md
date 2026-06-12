---
title: "Why different dialog boxes in gnome-shell?"
date: 2017-12-18
forum: Desktop Environments
---

### Post by jander on 2017-12-18
**This is a [COLOR="#FF0000"]duplicate[/COLOR]: see [https://ubuntuforums.org/showthread.php?t=2358715&p=13633967#post13633967]("https://ubuntuforums.org/showthread.php?t=2358715&p=13633967#post13633967")**. Thanks to Dennis N.



Hey,

I tried to google something about it, no luck!

I use Ubuntu 16.04 LTS, Gnome flavor, with the default file manager (Nautilus) in my desktop. 

When I use the open dialog box in many programs (gedit, libreoffice), I get the Nautilus-like view, with my bookmarks and so on.

[ATTACH=CONFIG]277863[/ATTACH]

But TexStudio uses a distinct dialog box, which is somewhat weird-looking and not functional (and also with none of my bookmarks):
[ATTACH=CONFIG]277864[/ATTACH]

Maybe it's a gtk-2 vs. gtk-3 issue?

GNOME Shell is 3.18.5, TexStudio is 2.10.8 (with Qt 5.5.1 R).

Is there a way to change that? I wasn't able to find where to configure. Thanks a lot.

Jander

Edit:
**The solution for my case:** just installed [FONT=Fixedsys]libqt5libqgtk2[/FONT].

---

### Post by Dennis N on 2017-12-18
The reason for the different dialogs is explained here:

[https://ubuntuforums.org/showthread.php?t=2358715&p=13633967#post13633967](https://ubuntuforums.org/showthread.php?t=2358715&p=13633967#post13633967)

You can't change the dialog style.

---

### Post by jander on 2017-12-18
Thanks! I'll take a look!

---

### Post by Dennis N on 2017-12-18
Just to add this: In qt applications, there are some tools that may work to change the look of the qt applications - see the last few posts in the thread linked in post #2.

---

