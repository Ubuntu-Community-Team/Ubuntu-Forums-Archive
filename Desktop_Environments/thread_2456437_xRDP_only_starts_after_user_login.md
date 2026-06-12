---
title: "xRDP only starts after user login"
date: 2021-01-11
forum: Desktop Environments
---

### Post by norcalwally on 2021-01-11
Hi Everyone- xRDP on Ubuntu Desktop 20.04, will only start after a user a logs in. I've run the command > [COLOR=#333333][FONT=Menlo]systemctl enable xrdp[/FONT][/COLOR], restarted, and no change. If I login with a user account on the Ubuntu desktop, and then attempt to connect via xRDP, then it works ok. As soon as I logout of the local Ubuntu session the service stops again

Feels like I'm missing something obvious, and I apologize in advance if this has been answered endlessly- I've been researching for 3+ hours.

---

### Post by norcalwally on 2021-01-11
Further troubleshooting shows that the service startup is tied to the admin login, no other user that logs in locally activates the xrdp service.

---

