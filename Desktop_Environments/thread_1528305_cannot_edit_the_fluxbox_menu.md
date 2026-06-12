---
title: "cannot edit the fluxbox menu"
date: 2010-07-10
forum: Desktop Environments
---

### Post by ice-brain on 2010-07-10
Hello, i have a question about fluxbox.
I wan't to edit the fluxbox menu. In the file ```
~/.fluxbox/menu
``` stands, that the file ```
/etc/X11/fluxbox/fluxbox-menu
``` is include.
So i edit this file and it works. But when i restart the XServer (or my Computer) the menu is the old. No changes from me are there.
What can i do?
PS: I hope you understand me, because my english isn't the best :)

---

### Post by hhh on 2010-07-10
I haven't used fluxbox but I've used openbox. I did some Googling, and it looks like you should only edit ~.fluxbox/menu. If you didn't backup the original /etc/X11/fluxbox/fluxbox-menu you can get it back by running
```
apt-get purge fluxbox
```
```
apt-get install fluxbox
```

There are two gui apps for editing the menu that you could try...
[http://fluxmenu.berlios.de/](http://fluxmenu.berlios.de/)
[http://code.google.com/p/fluxbox-menu-editor/](http://code.google.com/p/fluxbox-menu-editor/)

Sources I used for this post...
[http://fluxbox.sourceforge.net/docs/en/newdoc.menuedit.php#top](http://fluxbox.sourceforge.net/docs/en/newdoc.menuedit.php#top)
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

There is also this FAQ posted on the fluxbox wiki...
[http://fluxbox.sourceforge.net/docs/en/newdoc.menuedit.php#top](http://fluxbox.sourceforge.net/docs/en/newdoc.menuedit.php#top)

Verstehen sie? Bitte, ich nicht spreche Deutch.

---

### Post by urukrama on 2010-07-10
The file you are trying to edit (/etc/X11/fluxbox/fluxbox-menu) is automatically generated each time X starts, as it says in that file:

> # Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)

To change the menu you should copy the contents of /etc/X11/fluxbox/fluxbox-menu into your ~/.fluxbox/menu file. The /etc/X11/fluxbox/fluxbox-menu file encourages you to do so if you want to edit the menu file:

> # This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

If you do this make sure that your ~/.fluxbox/init file points to the right menu file and has this line:

> session.menuFile:	~/.fluxbox/menu

I believe this is like this by default, but it can't hurt to check.

---

### Post by ice-brain on 2010-07-11
Thanks for this info, urukrama. I will now edit the file ~/.fluxbox/menu ... I had copy the text from /etc/X11/fluxbox/fluxbox-menu and edit it in ~/.fluxbox/menu.

Thanks for your help

> Verstehen sie? Bitte, ich nicht spreche Deutch.
Is this a comparison to my english? ;)

---

### Post by hhh on 2010-07-11
> **ice-brain said:**
> Is this a comparison to my english? ;)
Lol, no, you can at least hold your own:^)

---

