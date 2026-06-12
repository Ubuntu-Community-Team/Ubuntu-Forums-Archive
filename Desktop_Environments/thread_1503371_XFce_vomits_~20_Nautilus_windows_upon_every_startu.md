---
title: "XFce vomits ~20 Nautilus windows upon every startup"
date: 2010-06-06
forum: Desktop Environments
---

### Post by RandomMatt on 2010-06-06
Hi (and sorry for posting two issues at once),

Whenever I start XFce, about 20 Nautilus windows also start up, choking the system and generally being a nuisance.

I don't even use Nautilus as my file manager under XFce, and whenever I try to delete it or set it not to run on the XFce session manager, it still appears on next startup.

I've tried to find where XFce stores its session information - deleting Nautilus shortcuts from ~/.config/session-state did nothing - and had no luck. Could someone please help?

Thanks,

Matt.

EDIT: I'm using Ubuntu (not xubuntu) Lucid.

---

### Post by drs305 on 2010-06-06
This was a bug in the very early stages of Karmic (I think).  I don't use Xfce but this worked with Ubuntu at the time. You can try to take the same approach to possibly make it work. At least until someone familiar with Xfce shows up.

To end it, run "killall nautilus" in a terminal until it stops spawning nautilus windows. You may have to run it multiple times (which makes the UP arrow key repeat terminal feature a plus).

To fix this, in Ubuntu I edited the following file as root:
[COLOR="Navy"]/usr/share/applications/nautilus.desktop[/COLOR]
and changed this line from "true" to prevent the autospawning:
> X-GNOME-AutoRestart=false 

Consider this, if it works for you, as a bandaid until you find out the reason for this behavior.

---

