---
title: "Make Gnome Default"
date: 2006-05-10
forum: Desktop Environments
---

### Post by totfit on 2006-05-10
I installed KDE and have somehow made it the default display manager. How can I change this back to Gnome. I am having problems with Open Office and I think that this could possibly be the cause. Anyway, I would hope that someone could give me or direct me to a source for the terminal commands to do this.

Thanks,
Gregg

---

### Post by Sef on 2006-05-10
>  	I installed KDE and have somehow made it the default display manager. How can I change this back to Gnome.

From the Konsole type this

kdesu aptitude installl gnome-desktop

At log in, click on session to change desktop manager.

Note: use aptitude instead of apt-get.  It will be easier to uninstall gnome if you so desire.

---

