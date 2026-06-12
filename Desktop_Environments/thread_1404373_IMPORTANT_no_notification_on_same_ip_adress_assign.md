---
title: "IMPORTANT: no notification on same ip adress assignment"
date: 2010-02-11
forum: Desktop Environments
---

### Post by someNewb on 2010-02-11
user gets absolutely no warning or notification when he connects to a wired network with the same ip as someone else who is online

i definitely think it should be fixed/implemented...

---

### Post by Zorael on 2010-02-11
[KDE bug tracker](https://bugs.kde.org) (requires registration)

Note that this may be a limitation in Network-Manager, in which case KDE devs can't do much but wait until that feature gets implemented. (KNetworkManager is just a frontend to Network-Manager.)

---

### Post by someNewb on 2010-02-11
are you sure? i'm think i'm running the default ubuntu gnome

edit: if kubuntu means kde ubuntu i'm sorry, i had no idea=S can someone retag this?

---

### Post by efflandt on 2010-02-11
If you are going to use static IP addresses, you should really have your own method of assigning/tracking them to avoid conflicts (and avoid DHCP assigned range).

---

### Post by lisati on 2010-02-11
> **efflandt said:**
> If you are going to use static IP addresses, you should really have your own method of assigning/tracking them to avoid conflicts (and avoid DHCP assigned range).

+1. I normally let my routers worry about IP address asignment, setting static addresses at the router if necessary, and leave my Ubuntu & Windows boxes to accept whatever they're given. One adavantage of doing it this way is that if I'm out and want to connect my laptop to someone else's network, there's less risk of conflicts.

---

### Post by someNewb on 2010-02-14
what does this have to do **anything** with ubuntu's defect and/or inability to warn user about duplicately assigned ip?

---

