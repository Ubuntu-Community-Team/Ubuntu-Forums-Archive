---
title: "connecting to server remotely using putty?"
date: 2009-04-21
forum: General Help
---

### Post by gazz1982 on 2009-04-21
I have my server up and running, no problems.

I am away from home at my office and I wish to login to my server using putty. At home I simply put in the IP address of the server. i use the external IP address and port number but I cannot connect, how can I do this?

My server is connected wirelessly (not ideal) to a router.

Thanks

Gary

---

### Post by amingv on 2009-04-21
Have you set up your router to forward requests to port 22 to your server? If you haven't most likely they're getting dropped by NAT/firewall in the router.

---

### Post by sefs on 2009-04-21
> **amingv said:**
> Have you set up your router to forward requests to port 22 to your server? If you haven't most likely they're getting dropped by NAT/firewall in the router.

Also if a firewall is running on the server you will need to open a port in the firewall.

---

