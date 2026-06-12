---
title: "not automatically updating apt"
date: 2008-01-07
forum: Debian
---

### Post by maybeway36 on 2008-01-07
I'm using Debian lenny with Adept Notifier. When I look at the file /etc/apt/apt.conf.d/15adept-periodic-update, it says:
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
```
There is a file just like this in Kubuntu, and there it works just fine. However, in Debian it's not working at all. I have to manually apt-get update before Adept Notifier sees any updates.
Also see: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422564]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422564")

---

