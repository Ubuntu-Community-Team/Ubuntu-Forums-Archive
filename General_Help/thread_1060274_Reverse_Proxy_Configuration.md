---
title: "Reverse Proxy Configuration?"
date: 2009-02-04
forum: General Help
---

### Post by RockStrongo on 2009-02-04
Hi - I am trying to configure a reverse proxy using two ubuntu servers (host1 and host2).   One server, host1, is accessible externally via my.examplesite.org, however host2 is not.  So, I would like to be able to hit "my.examplesite.org/app1/" and have reverse proxy the application "app1" that is running on host2.

How do I do this in Apache?   I found some documentation on VirtualHosts, but I was not clear on how to configure it..

<VirtualHost *:*>
ProxyPreserveHost On
ProxyPass / [http://192.168.111.2/](http://192.168.111.2/)
ProxyPassReverse / [http://192.168.111.2/](http://192.168.111.2/)
ServerName hostname.example.com
</VirtualHost>

---

