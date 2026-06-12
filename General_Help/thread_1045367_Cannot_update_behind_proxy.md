---
title: "Cannot update behind proxy"
date: 2009-01-20
forum: General Help
---

### Post by Graham1 on 2009-01-20
Hi

I'm trying to update Ubuntu 8.04 behind a proxy but it keeps failing with "111 Connection refused".

I've entered the following under "Network Proxy" (Preferences):-

Manual proxy configuration
HTTP proxy: <ip><port> (ip and port of proxy)
Authentication: <domain>\<username> (username includes "." between firstname and surname) and <password>

Am I doing something wrong? Any advice?

:)

Edit: Btw, if I enter the above authentication into Firefox (when prompted), I can browse the internet fine.

---

### Post by linux_tech on 2009-01-20
Open Synaptic, then go to Settings > Preference > Network. Enter your manual HTTP proxy config : 
user:[email]password@proxyloc.net[/email], then the proxy server port- try 8080 , click apply

[http://ubuntuforums.org/showthread.php?t=83401](http://ubuntuforums.org/showthread.php?t=83401)

---

