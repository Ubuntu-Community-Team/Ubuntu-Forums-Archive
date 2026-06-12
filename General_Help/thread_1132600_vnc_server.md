---
title: "vnc server"
date: 2009-04-22
forum: General Help
---

### Post by pawan_lal on 2009-04-22
hi friends,
i want to set up a  vnc server in my ubuntu 8.04LTS edition. ne help will be highly apreciated.
Regards,
Pawan

---

### Post by Menschenfresser on 2009-04-22
If you are using the desktop version then there is one installed by defaut. Perhaps you have to activate it (look in the settings menu something like "remote desktop")

---

### Post by uncle-c on 2009-04-22
You will know if you are running vncserver on your local machine if you get output similar to :

```

unclec@unclec-desktop:~$ lsof -i 
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
vino-serv 7183 unclec   16u  IPv6  34356       TCP *:5900 (LISTEN)

```

VNC Server  port 5900 is open and listening for any connection.

---

