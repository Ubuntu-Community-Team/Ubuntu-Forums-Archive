---
title: "why the IP address changes?"
date: 2009-06-22
forum: General Help
---

### Post by mmbathan on 2009-06-22
**Hi guys **
 
**I connect to machines using cross cable with static IP address in bridge mode.**
**I run VMware and ubuntu in both machines.**
 
 
**the problem in one of the machines the IP address sometime is changed by it self and take IP from the wireless while if I disconnect the wireless and configure the IP addess again in sometime the IP address is changed without IP address.**
 
**what do think guys the problem?**

---

### Post by HermanAB on 2009-06-22
You likely have dhclient running.  DHCP is a protocol that is commonly used to assign IP addresses and your WiFi router likely has a DHCP server running.  So the system is working as it would normally be expected to.

---

### Post by lovinglinux on 2009-06-22
> **HermanAB said:**
> You likely have dhclient running.  DHCP is a protocol that is commonly used to assign IP addresses and your WiFi router likely has a DHCP server running.  So the system is working as it would normally be expected to.

As explained above, the DHCP will assign the IP to each machine by order of connection. If you want to make the IP of each machine static go to "System >> Preferences >> Network Connection" and set the connections manually.

---

### Post by pbpersson on 2009-06-22
If you ever shut your machine down, when it boots up it will get a brand new IP address.  I believe that is the rule.  An IP address handed out using DHCP is actually "leased" and it has an expiration time.  My machine is up all the time, 24 hours a day.  If I look in my syslog I can see my machine asking if it can keep the same IP address each time the lease expires so it always keeps the same address:

```
Jun 21 16:04:30 Ubuntu-desktop dhclient: DHCPREQUEST of 192.168.0.105 on eth0 to 192.168.0.1 port 67
Jun 21 16:04:30 Ubuntu-desktop dhclient: DHCPACK of 192.168.0.105 from 192.168.0.1
Jun 21 16:04:30 Ubuntu-desktop dhclient: bound to 192.168.0.105 -- renewal in 10643 seconds.
```

---

### Post by mmbathan on 2009-06-22
> **lovinglinux said:**
>  If you want to make the IP of each machine static go to "System >> Preferences >> Network Connection" and set the connections manually.
 
**thank you guys I'll try this and see what happen.**
 
**Regards,**

---

### Post by lovinglinux on 2009-06-22
> **mmbathan said:**
> **thank you guys I'll try this and see what happen.**
 
**Regards,**

You are welcome. 

Please don't use bold letters on your posts. Nobody does, unless you need to highlight parts of your text.

---

