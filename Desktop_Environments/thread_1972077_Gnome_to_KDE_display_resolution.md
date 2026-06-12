---
title: "Gnome to KDE display resolution"
date: 2012-05-03
forum: Desktop Environments
---

### Post by andreysantana on 2012-05-03
Hey y'all! :)

I'm having some trouble setting my display settings on my ubuntu, right after installing KDE.
Everything was fine when using Gnome, from a scratch install of Ubuntu 11.10.
I decided to install KDE to give it a try. On KDE, the nvidia x server settings detects that my display has 1920x1200, but for some reason the icons and fonts are HUGE!! 

So, after googleing here and there, I found a thread saying I should edit /etc/X11/xorg.conf and add an entry "Virtual 1920 1200"

I did as suggested, and clicked on a script called Xreset on the same folder.
All of the sudden, as I closed and reopened applications, the display seemed correct to me.
The problem was when I had to restart the machine, Xserver couldn't start. So, I changed the file again, deleted the entry, restarted the computer, and voilá... back to huge icons and fonts :(

Needless to say, I'm a newbie so I'm kind of shooting in the dark here.. Can someone help me?

Much appreciated!

Andrey

---

