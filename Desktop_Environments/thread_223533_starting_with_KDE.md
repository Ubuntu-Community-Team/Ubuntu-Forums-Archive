---
title: "starting with KDE"
date: 2006-07-26
forum: Desktop Environments
---

### Post by AndEat on 2006-07-26
How do I get programs to start when logging into KDE?

---

### Post by wieman01 on 2006-07-26
Same way as in Gnome... Either use the menu or the terminal firing them up with a line command.

---

### Post by ltmon on 2006-07-26
EDIT: I read your post as meaning how do you get a program to automatically start whenever you log on to KDE.  If this isn't what you meant, sorry :)

There are two main ways I know of:

Firstly is the KDE session.  By default it remembers which programs were running when you logged out last and fires them up again when you log in again.

You can tweak this behaviour in "System Seetings -> KDE Components -> Session Manager".

Otherwise you can put a link to an application in the hidden folder ~/.kde/Autostart.

The easiest way to do this is to open a konqueror file browser window and point it to: "~/.kde/Autostart" (type it in to the address bar).

Next, drag and drop an application from the K Menu to the autostart window.  When you drop it you will have an option to "Link Here".  Choose that and you are on your way.

Cheers,

L.

---

### Post by AndEat on 2006-07-27
thx much

That's the info I was searching for to get me started.


:D

---

