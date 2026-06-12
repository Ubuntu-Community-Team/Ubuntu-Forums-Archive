---
title: "xdmcp keyboard wrong mapping after remote login"
date: 2009-06-05
forum: General Help
---

### Post by josetavares on 2009-06-05
When I connect to Ubuntu jaunty machine via xdmcp from any machine of the same network, I'm able to login with no issues but, when I get the gnome desktop , my keyboard mapping seems to be all messed up.

---

### Post by cupinzim on 2009-08-18
I got the same problem, using Ubuntu 9.04 server on a HP Proliant + HP 5735 Thin Clients.
If I log physically into the server, the keyboard works perfectly, the same happening if I log physically into the Thin Clients (both using Brazilian ABNT2 keyboards).

But if I log into the server using the Thin Clients through XDMCP, the keyboard settings vanish away!

Does anyone know the solution?

---

### Post by josetavares on 2010-04-14
Cooking. Rename the /usr/bin/xmodmap on the server, boot the box and try again to get a remote windows from your server.

---

