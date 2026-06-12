---
title: "simulate net access to stop disconnect"
date: 2009-04-16
forum: General Help
---

### Post by ubuntumaybe on 2009-04-16
Hi,

I get my internet connection in a library. If I do not access the net within 10mins I am disconnected. I then have to reboot to get the connection again. I am looking for an app that will simulate intenet access over a certain set time, e.g. 8 mins. Any ideas? Thanks.

joe

---

### Post by HermanAB on 2009-04-16
Hmm, I'd make a crontab and do a single ping or wget to [www.yahoo.com](www.yahoo.com) every 3 minutes.

---

