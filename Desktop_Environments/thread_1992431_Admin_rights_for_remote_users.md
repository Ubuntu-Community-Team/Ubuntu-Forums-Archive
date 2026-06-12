---
title: "Admin rights for remote users"
date: 2012-05-31
forum: Desktop Environments
---

### Post by jbuller on 2012-05-31
I have a fresh install of 12.04 i386 Desktop and have installed xrdp so I can remote desktop instead of using VNC.  Unfortunately when I rdp to my machine I can not perform and system maintenance.  My understanding is this is how Polkit treats remote users.  My desktop runs in VMware and I do not want to use the VMware console every time I need to do something on this system.

Does anyone know how to configure Polkit so remote users have the same rights as local users?

I have already tried changing <allow_inactive>no</allow_inactive> to <allow_inactive>auth_admin</allow_inactive> or just plain yes with no change at all.  I made a local policy as per [http://scarygliders.net/2012/05/23/the-scarygliders-x11rdp-o-matic-and-rdpsesconfig-hotness-upon-hotness/](http://scarygliders.net/2012/05/23/the-scarygliders-x11rdp-o-matic-and-rdpsesconfig-hotness-upon-hotness/) but again no love.

---

