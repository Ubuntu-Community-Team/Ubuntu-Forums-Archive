---
title: "Xubuntu / xfdesktop and panel uses up too much memory"
date: 2006-07-06
forum: Desktop Environments
---

### Post by rshetye on 2006-07-06
Every 72 hrs or so I have to log out and restart my XFCE session, otherwise the session keeps degrading and eventually becomes unusable.

At some point, xfdesktop starts using 100+ MB of actual physical memory (not virtual memory), and one of the panel executables also starts using 100+ MB of RAM.

I used htop to verify the memory usage. There's a leak somewhere in the XFCE desktop libraries ?

---

### Post by nublaii on 2006-11-21
I have that problem too, and apparently yes, there is a memory leak (saw it somewhere on xfce's bug tracking list).

You don't need to log out to get all that memory back.

The problem seems to be with the menus: there are two of them, the menu on the menubar and the one that appears when you right-click.

If you have the 'Xfce menu' on the bar you have to remove it and then re-add it.

Then, open a terminal and type 'xfdesktop -quit' and then 'xfdesktop &'. You can quit the terminal because you'll get a bunch of GTK errors.

It's a very very dirty fix, but it's better than login out and login-in again.

---

### Post by paul cooke on 2006-12-09
I couldn't do anything... forced to ctrl alt backspace. I'd been running xmms all night and found the machine almost locked up... xmms was still running fine though.

---

