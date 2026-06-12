---
title: "ask for password in shortcut"
date: 2008-05-15
forum: Desktop Environments
---

### Post by prd on 2008-05-15
Hi, 
I am trying to make it easier to login into my vpn. I have made a shortcut to "vpnc-connect office". I don't want to put password at office.conf file, and I want it to ask for password everytime I connect.
It is working at terminal, but I want to make it working as shortcut. So I can just click "connect" and it will ask password, and connect. Or may be, shows a terminal screen, ask the password, connect, then close the screen.

Any idea how to do it? Thanks

---

### Post by sdennie on 2008-05-15
If you created a launcher you could try right clicking on it, going to properties and changing "Type" from Application to Terminal Application.  Then just change the command line in that window to ask for the password just like you'd do from the command line.

---

### Post by prd on 2008-05-19
Thanks..that works.

---

