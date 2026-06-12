---
title: "Error Message Re: Gnome/Daemon Settings"
date: 2008-04-28
forum: Desktop Environments
---

### Post by VickiAnn on 2008-04-28
I changed the groups I belonged to yesterday in trying to get something else to work - but haven't changed them back because I've actually forgotten which I should belong to as default but now when I login - I get this error message:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Does anyone know how I can solve this?

I am not a member of the group with daemon in the name - that's the first thing I did to try and solve this.

---

### Post by VickiAnn on 2008-04-28
I've managed to fix this - it seems to be a common bug and turns out my etc/hosts/ file and /etc/network/interfaces/ files were missing some info.

:D Now all working :D

---

### Post by Kaphius on 2008-04-29
> **VickiAnn said:**
> I've managed to fix this - it seems to be a common bug and turns out my etc/hosts/ file and /etc/network/interfaces/ files were missing some info.

:D Now all working :D

How did you manage to fix it?:confused:

---

### Post by jjthomas on 2008-04-30
> **VickiAnn said:**
> I've managed to fix this - it seems to be a common bug and turns out my etc/hosts/ file and /etc/network/interfaces/ files were missing some info.

:D Now all working :D

:confused:  How about posting the solution????

Thanks.

-JJ

---

### Post by DeFKnoL on 2008-05-06
VickiAnn was just helpful enough for an experienced Linux user like myself to figure it out.  It would have been nicer if she actually posted the solution rather than a tease.

Anyway,  I fixed it by doing the following:

made sure that /etc/network/interfaces had the following two lines:

```

auto lo
iface lo inet loopback

```

and /etc/hosts needed this line:

```

127.0.0.1     localhost

```

the localhost address is the loopback address

---

