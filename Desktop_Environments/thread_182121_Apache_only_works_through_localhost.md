---
title: "Apache only works through localhost?"
date: 2006-05-25
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-05-25
How come I can only access my webserver/ftp server through localhost.

I've double checked the static ip with my ISP, it should be OK.

I have no firewall/router blocking the ports.

It must be a config error somewhere? Does anyone have suggestions to solve this? (Just to work earlier, then I installed mysql-server, and then it became localhost only. I reinstalled everything (apache/php/mysql), still the same prob.)

Thanks in advance.

---

### Post by DarthMandeep on 2006-05-25
I don't use apache, but in lighttpd an option in the config file is to bind the server to localhost only. Apache most likely has a similar option. Look through your apache config file and see if there's a "bind" line. Comment that out and restart apache to check if that's the problem.

---

### Post by stiankarlsen on 2006-05-25
There is such an option, but it's not bound to localhost only, it's set to listen on everything on port 80, so it should be ok. I tried setting it to port 5000, but that didn't help either.

---

### Post by stiankarlsen on 2006-05-25
There's really nothing I could try?

---

### Post by DarthMandeep on 2006-05-26
Can machines on the local network access the web server?

---

### Post by stiankarlsen on 2006-05-26
I think so, but I had a friend try it from a totally different location, and that didn't work either.

---

### Post by romUdog on 2006-05-27
I have the same problem except i go through ICS (internet connection sharing) via windows XP pro (SuckY!) but anyway anyone got any ideas...im all for it!, lol btw my ftp just wont work either >.> linux is not meant for kids like me...LOL!!!

---

