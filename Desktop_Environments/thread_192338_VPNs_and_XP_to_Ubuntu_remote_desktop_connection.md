---
title: "VPNs and XP to Ubuntu remote desktop connection"
date: 2006-06-08
forum: Desktop Environments
---

### Post by spyke01 on 2006-06-08
Hi guys, i got information on connecting to my xp workstation via vpn, but forgot to get info for doing it the other way. Im thinking just enable it via adminsitration->remote desktop and remote desktop from the xp via the ubuntu boxes ip, is this correct?

---

### Post by scxtt on 2006-06-08
that sounds more like VNC, not VPN ... if you've got vncserver/vncviewer installed on both machines you can VNC between them ... and yes, if vncserver is running on a box, you'd do:

vncviewer <server ip-address>:<screen #, given to you when you start the server>
(ex. vncviewer 192.168.1.100:1)

from the box you're using as the client ... and don't forget about firewalls and port forwarding ...

---

