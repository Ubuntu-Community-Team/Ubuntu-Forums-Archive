---
title: "How to get VPN connection info?"
date: 2013-02-14
forum: Desktop Environments
---

### Post by KooriNyann on 2013-02-14
Hi,
My English is not good, and i will try my best to describe the question.

I am now using an ubuntu-Desktop enviroment.
 
When connecting VPN Server, it would show very little information about connection status, when failed or disconnected with VPN Server, it just tell me that It was failed to connecting server or the VPN network was disconnected.

But I am not willing to get this info at all, what i need is why i failed with it? or why I was disconnected. is my password wrong? should i checkout whether my Huber was down or just the VPN server has crashed...

I think there must be a way to get those information...
please tell me how with thanks.

---

### Post by ali abry on 2013-02-15
logs about these things goes to /var/log/syslog
you can run this command before trying to connect to vpn  :

```
 tail -f /var/log/syslog
```this command will show you output appended  data  as  the  file  grows .

---

### Post by slickymaster on 2013-02-15
The information for each connection is stored in the gconf preferences database, on a per-user basis. If you need to edit this manually, run **Applications/System Tools/Configuration** editor (or gconf-editor from a terminal). Connections are stored under ```
system/networking/vpn_connections
```

---

### Post by KooriNyann on 2013-02-15
Thanks a lot for your kindly help, and the problem is now completely solved:)

---

