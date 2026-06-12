---
title: "can't add network interface in network administration"
date: 2005-04-28
forum: Desktop Environments
---

### Post by revolthor on 2005-04-28
i am trying to use a dlink pcmcia wireless card with my aluminum powerbook (since airport extreme isn't supported)  i've got all the drivers and whatnot compiled, but thet network administration program in gentoo does not have an "add" button like it does in the help pages, and i cannot figure out anyother way to add and configure a network interface.  any help is much appreciated.  thanks!

---

### Post by alastair on 2005-04-28
What do you mean : 

> but thet network administration program in gentoo does not have an "add" button"

You are using Ubuntu aren't you? If not - try the Gentoo forums.

If yes - re-submit in the networking forum - but post some details i.e.

Log messages from /var/log/syslog - look for the networking being probed/discovered.

Also, things like :

ifconfig -a
iwconfig

---

