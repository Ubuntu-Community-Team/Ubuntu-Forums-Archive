---
title: "force apps menu to appear in their own window not in the top taskbar"
date: 2011-05-11
forum: Desktop Environments
---

### Post by rvboutin on 2011-05-11
Hi,
I have searched with no luck the forum, maybe I used the wrong keywords...
Anyway, in Unity (that I am trying to like :) ... difficult though! :(), is there any possibility to have each applications (open window) to have its own menu bar instead of having the active apps menu going into the taskbar... I am finding this really annoying! ](*,)
That partly why I use the classic gnome desktop and not Unity (but I don't want to trash it without trying :P:p
Cheers,
Rv

---

### Post by Krytarik on 2011-05-11
See here on how to disable the Global Menu for all or specific apps:
[http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html](http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html)

Greetings.

---

### Post by rvboutin on 2011-05-11
see below, Krytarik is right I should have posted on the forum... so here is a message which can be useful :D
Quote:
Originally Posted by rvboutin
Hi,
Thanks for replying, I also found this: [http://flnkr.com/2011/05/09/disable-ubuntu-11-04-unity-global-menu/](http://flnkr.com/2011/05/09/disable-ubuntu-11-04-unity-global-menu/)
which seems less complicated... but is it safe/correct?
cheers,
Rv

Reply: Yeah, it's another way to in fact remove one responsible package, I have also posted that as a solution sometimes, although with "apt-get" instead of "dpkg".

But now I prefer the soft way, by only disabling it, and in fact the respective commands are not that much more complicated :
Code:
```
sudo su
```
```
echo "export UBUNTU_MENUPROXY=" > /etc/X11/Xsession.d/81ubuntumenuproxy
```
Greetings.

PS: The next time, please post in the thread, so that other users can benefit from it as well.
__________________
Troubleshoot and Customize Unity/Natty
Tweaks/Fixes for Unity after Installing
The Power User’s Guide to Unity

---

