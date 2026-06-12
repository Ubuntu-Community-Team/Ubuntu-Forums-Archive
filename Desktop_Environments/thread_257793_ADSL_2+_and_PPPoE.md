---
title: "ADSL 2+ and PPPoE"
date: 2006-09-15
forum: Desktop Environments
---

### Post by jibril on 2006-09-15
Hi there guys, 

I tried connecting to my ISP using an ADSL2+ modem but I have absolutely no idea how to d the PPPoE as when I opened the Network Configuration of Ethernet .. There was no such option mentioned!!!

I want to enjoy the goodness of my 11Mbps connection ..,, Please Help :(

Jibril

---

### Post by Jucato on 2006-09-15
In the Terminal, enter the command

```
sudo pppoeconf
```

This will configure your ADSL connection. You can safely accept the default answers/settings for those questions you don't know the answers to.

---

