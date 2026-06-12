---
title: "Global way to set proxy"
date: 2006-01-10
forum: General Help
---

### Post by h.mehdi on 2006-01-10
Hey all,

Is there any way to set proxy for all app's in Gnome ? I've set proxy like this :
export http_proxy=http://username:pass@proxyserver:port/
export ftp_proxy=http://username:pass@proxyserver:port/
in my .bashrc file, now `wget' and `apt-get' work fine with proxy, BUT I have problems with other app's...

Is there any way to set proxy in Gnome ?

---

### Post by schilcha on 2006-01-10
Have a look at the System-Menu -> Preferences -> Network Proxy

---

### Post by lamego on 2006-01-10
Please note that some applications have specific configuration files to define the proxy, not to mention that a few don't even support it.
For terminal apps usually you can find that info on the man pages .

---

### Post by h.mehdi on 2006-01-10
Thanks Guys
Works like a charm :D

---

