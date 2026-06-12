---
title: "Cisco CCNA labs"
date: 2018-12-19
forum: Education &amp; Science
---

### Post by nissen on 2018-12-19
Hi, 

I'm doing some CCNA labs and I'm having trouble reading a extended ACL properly. Actually its the last part I don't really understand.  

 ACL command I shall execute: 
GAD(config)#access-list 101 deny tcp 192.168.14.0 0.0.0.255 **any eq 80**

The ACL written in text: deny tcp traffic from network 192.168.14.0 with wildcardmask 0.0.0.255 to any port 80?

I don't understand why "any" is before "eq 80". 

Can someone explain me why?

---

### Post by The Cog on 2018-12-19
It means deny tcp from 192.168.14.0/24 (any port number because it's simply not specified) to any destination address port 80.
The word **any** where an IP address is expected gets expanded to **0.0.0.0 255.255.255.255**

---

### Post by nissen on 2018-12-23
> **The Cog said:**
> It means deny tcp from 192.168.14.0/24 (any port number because it's simply not specified) to any destination address port 80.
The word **any** where an IP address is expected gets expanded to **0.0.0.0 255.255.255.255**

Thank you for explanation :) 


Merry Christmas :)

---

