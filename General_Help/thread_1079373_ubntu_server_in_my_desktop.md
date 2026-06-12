---
title: "ubntu server in my desktop"
date: 2009-02-24
forum: General Help
---

### Post by david sousa on 2009-02-24
I have a desktop and a laptop with ubuntu. I can connect them by ssh with internal ip adresses. but i would like to access my desktop out of my house. How do i do that?

---

### Post by taurus on 2009-02-24
Are your computers connected to a router?  You need to open a port on your router for incoming signal and forward that to your desktop machine, assuming you have already installed ssh-server (sshd).

---

### Post by makisupa123 on 2009-02-24
Also make sure that you know your external IP address ([www.ipchicken.com](www.ipchicken.com) -- sounds funny, but you'll remember it).

With most residential ISPs this will change every 2 weeks to 2 months.  In that case, you may want to look into a dynamic DNS service like "dyndns".  Many routers can be configured to use services like this and update your DNS entry when your IP changes.

--Mak

---

### Post by david sousa on 2009-02-24
Ok thanks, now, i have installed ssh-server an i know my external ip adress. how do i do this?

---

### Post by taurus on 2009-02-24
What about a router?  Is your desktop connected to a router?  You need to open a port for incoming signal or your won't be able to ssh to your desktop from outside.

---

### Post by david sousa on 2009-02-24
i have all my pcs connected to a router by wireless. how do i open a port?

---

