---
title: "avahi problem"
date: 2009-04-20
forum: General Help
---

### Post by abandonow on 2009-04-20
Hi, I have a working afp share set up with netatalk, and running avahi to broadcast some of the services on the server (mainly netatalk afp and vnc).

Anyhow, after reboot the netatal afp share does not show up in finder, but if I restart the avahi daemon it shows up.. so things are working.

I thought it could be that the avahi daemon starts after the netatalk daemon, so I went in to /etc/rc.1 to 5 and changed the number so netatalk started first (they had the same number), but still no go.

Anyone that could think of a solution?

Thanks!

---

