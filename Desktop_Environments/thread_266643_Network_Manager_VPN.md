---
title: "Network Manager VPN"
date: 2006-09-27
forum: Desktop Environments
---

### Post by seekyrr on 2006-09-27
I do not see a VPN option in the network manager drop down menu.

Is there something specific I need to add/configure?


Thanks

Seek

---

### Post by marianom on 2006-09-27
I think you need to install one.
For example: openvpn  [http://openvpn.net/](http://openvpn.net/)

---

### Post by seekyrr on 2006-09-29
Found the setup here but not sure the exact command.  Can somone post the way to install the openvpn plugin plse.

VPN support
NetworkManager VPN support is based on plug-in system. You can download some plugins (cisco vpn, openvpn, pptp) form [WWW] **[http://bootlab.org/~j/NetworkManager/](http://bootlab.org/~j/NetworkManager/)**
 There are build for debian but they work very well on my Ubuntu 6.06, no warning, no errors... just be sure to restart your networkmanager daemon. 

Seek

---

### Post by fago on 2006-10-02
I tried the pptp plugin but had no success. When I tried to connect to the vpn server, I got these errors on syslog:

```
Oct  2 12:53:10 localhost pppd[28148]: /usr/lib/pppd/2.4.4b1/nm-pptp-service-pppd-plugin.so: cannot open shared object file: No such file or directory
Oct  2 12:53:10 localhost pppd[28148]: Couldn't load plugin nm-pptp-service-pppd-plugin.so
```

I'm from austria and most dsl providers here are using pptp. So it would be really important to have an easy way to configure pptp vpns - this could be the solution...

Unfortunately configuring pptp-linux & pppd isn't that easy.

---

