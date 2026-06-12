---
title: "System Hang If I Log Out And Back In"
date: 2009-02-25
forum: General Help
---

### Post by vahnx on 2009-02-25
I just installed Ubuntu 64 the other day on this new PC and it's set to auto-login which works fine. If I log out and back into gnome, the system will hang. I can log out and into xfce4 fine though. When I try to log into KDE4 it stops at the 4th loading icon so I removed KDE.

This is very troublesome as I've experienced system hangs in the past and ended up frying machines from hard power offs. So I'll probably end up removing Ubuntu if this continues, or could someone recommend a different distro?

Thanks.

---

### Post by blueridgedog on 2009-02-25
What error logs have you looked at for clues?

I would review /var/log/messages and /var/log/Xorg.N.log where N is a number.  I do not know any KDE specific logs as I do not run it.

---

