---
title: "Second X session has limited video acceleration"
date: 2006-07-14
forum: Desktop Environments
---

### Post by titoose on 2006-07-14
My computer is shared by two users, but only the first one gets 3D acceleration. Video playback is too slow for the second session (2D acceleration problem too?).

In Xorg.1.log I got line like this (not continous):

```
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6
(EE) fglrx(0): Hardware already been locked.
```

---

### Post by Anduu on 2006-07-14
Go to System>Administration>Users and Groups>

Highlight the second users name and click properties>user privelages and check to make sure "Use video aceleration" is enabled.

---

### Post by titoose on 2006-07-15
Both users have those privileges, but only the first user starting session can watch video files without glitches or use 3D acceleration. 

My desktop is KDE with kdm as session manager, and the video driver is the ATI propietary one (fglrx). 

THANKS!!!

---

### Post by Anduu on 2006-07-15
Hmmmmmmmm...well I don't know much about KDE....

I do seem remember seeing some posts similar to yours a while back...try some searches and see what you come up with.

---

### Post by titoose on 2006-07-15
OK, seems that the first user owns the hardware resources, and the next X sessions can't access to these resources. In Windows XP this is not a issue, and I think that in Mac OS X either, so may be in linux it could be solved but I don't know how to.

My question is: is it possible to configure kdm or gdm to not spawn new  X session and force to all users to share the same session (display=:0)?

I think this can be related with the removable devices problem, because this kind of problem occurs with usb memory devices or ipods too, being the first user that starts a linux session the only one capable of mounting or reading these devices.

Note: I've been using linuxes-unixes during years in the server side, but I switched to desktop (Kubuntu Breezy and now Dapper) a year ago. It seemed that almost all was OK, but this problem could bring me back to dark times of Windows XP :_(

---

### Post by titoose on 2006-10-16
I'm very sorry, but after 13 months with only linux on my computer, this problem makes me install Windows... again. I was looking for info about this issue and it seems to be a X system issue with no fix nor workaround in near future.

I solved other problems related with concurrent users (e.g. ipod mounted only by first logged user, same with USB memory devices), but for this I could not find a solution. For solving this I suppose that user swithing must be performed without create new X session, you must instead redirect all X output of switched session programs to a dummy DISPLAY instance, and then reopen the first X session (the one that owns the video resources), with new session programs render to this DISPLAY. I think Windows does something similar. I think this aproach implies a lot of work on session managers and security system.

Likely I'm saying a lot of nonsenses ;) but I miss Amarok, XGL and the linux console.

See all you soon.

---

