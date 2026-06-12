---
title: "Use mobile-broadband instead of wired-connection for Internet"
date: 2010-12-01
forum: Desktop Environments
---

### Post by ubuntwinkel on 2010-12-01
This is an intriguing question, I hope.  I would dearly love to have it answered.

I have a LAN at home, with a fairly dependable Internet connection.  However, when the Internet connection goes down, I can connect via bluetooth DUN using Blueman and Network-Manager, but only if I dosconnect the wired-connection (LAN).  I run Lucid.  

In other words, when my cable Internet is down, and my wired-connection is still connected, then Network-Manager will not use the mobile-broadband connection for Internet, and instead keeps trying the LAN gateway for an Internet connection.  And fails.  Even though I can connect to the Internet over mobile-broadband **IF** I disconnect the wired-connection.  

Is there a way to stop Network-Manager from preferring the wired-connection for Internet when the LAN's Internet is down?  

The simple answer is, "Disconnect the wired-connection."  But I need the LAN for other servers in my house.  

I have attacked this from every possible direction, and searched and searched, to no avail.  I guess that Network-Manager cannot tell whether there is an Internet connection beyond my router (the LAN).  But shouldn't it be able to detect that the wired Internet connection (via LAN) has failed, and gracefully transition to the working Internet connection (via mobile-broadband)?  Is there such a thing in Network-Manager as connection pooling?

Any answers, even a decisively negative one, would be welcome.

---

