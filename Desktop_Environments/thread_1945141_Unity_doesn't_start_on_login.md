---
title: "Unity doesn't start on login"
date: 2012-03-22
forum: Desktop Environments
---

### Post by Howy on 2012-03-22
Ok, I've searched around, but none of the topics I've seen suit my case, so here goes:
I use Unity, and have done so since Natty. However for some time it has been malfunctioning, specifically in the way that when I log in in a normal way, no tricks up in the session, only starting through the default way, it doesn't show Unity or any window manager/Compiz. Windows start without a border, and I see Nautilus' menu on top. Keyboard focus is broken, and yeah.
I know it can't be a problem with my hardware performance, and I know it's not a direct incompatibility since I can start it through a workaround. (ssh+export display or add it to startup entries)
However these seem to add a LOT of unnecessary loading time. For quite some time, only the wallpaper shows, and I have to wait for the usual startup entries to get running before Unity pops up. (Gnome Shell pops up in 2 seconds after hitting enter, for comparison.)
The first command it attempts is the regular syntax:
```
gnome-session --session=ubuntu
```
This one doesn't seem to work well in this case, as all I get is the clear screen. I also guess I can't just make it start up with simply the "unity" command? (It won't show up in the menu if I use it as the first one.)

I've been wondering if I should make an xinit.rc file for Unity which I put in a separate entry. (Of course)

I'll also post some debug information from running "gnome-session --session=ubuntu" later.

Useful to know:
I got one of the latest fglrx drivers, built from AMD's site. (Don't worry, I made a .deb package specifically for Ubuntu. It's all set up properly and neatly.)
Just ask for more information if needed.

My current workaround:
```
#!/usr/bin/env bash
unity &
gnome-session --session=ubuntu
```
This works currently, but is neither safe or really compatible with future changes.
However from the output of the gnome-session command, I did get a couple of hints. First is that Unity doesn't seem to be in the procedure at all, it's not started by it. The script above does make my login faster and also keeps the desktop intact for now (None of the ugly icons show), but again, I would need a better solution for it to be more future-proof.

---

