---
title: "Stop unwanted services, make my server run faster"
date: 2006-07-16
forum: Desktop Environments
---

### Post by horatiub on 2006-07-16
Hello everybody. Currently, I'm running an email server and a web server on my Drake linux box powered by a P3 1.0Ghz, 256MB RAM.
I noticed that sometimes I get really slow response from my server, probably due to not enough memory and slow CPU, but I also noticed that I have a lot of services running in the background that I probably don't need e.g Printing Services, Samba, etc..
How can I stop these services from loading at boot? Can somebody walk me throught?

Thank you

---

### Post by Ramses de Norre on 2006-07-16
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
You can select/deselect services there, the runlevel you boot in normally is two and services under S or s are started in every runlevel.
Be careful while turning of services and only do so when you're sure what they do. Deselecting important services can break your system!

---

