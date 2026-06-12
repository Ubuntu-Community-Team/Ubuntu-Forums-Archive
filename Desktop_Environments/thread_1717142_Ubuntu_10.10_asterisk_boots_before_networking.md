---
title: "Ubuntu 10.10 asterisk boots before networking"
date: 2011-03-29
forum: Desktop Environments
---

### Post by ucido on 2011-03-29
I have my asterisk server logging into a SIP call provider on the network.  The problem is that asterisk is running before the network is up and so the DNS resolution for the SIP call provider fails and shuts down the login.  If I restart asterisk it all works.  Any ideas?
 
Thx
O-

---

### Post by doctorzeus on 2011-03-29
> **ucido said:**
> I have my asterisk server logging into a SIP call provider on the network.  The problem is that asterisk is running before the network is up and so the DNS resolution for the SIP call provider fails and shuts down the login.  If I restart asterisk it all works.  Any ideas?
 
Thx
O-

Add a bash start-up command to re-start asterisk on start-up perhaps? 

Or a better option might be a delay-start-up command (sleep function perhaps)?

---

