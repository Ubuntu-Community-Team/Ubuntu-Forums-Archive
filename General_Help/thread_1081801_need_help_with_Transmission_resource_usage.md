---
title: "need help with Transmission resource usage"
date: 2009-02-26
forum: General Help
---

### Post by bayonetblaha on 2009-02-26
Even with 2GB of RAM and dual-core, I'm having a lot of trouble with text entry freezing up and such, and I'm pretty sure all my resources are going to Transmission.  How can I get Transmission to pause all and resume only when my computer is idle? This seems like the best solution not only for my problem but anyone concerned about browsing bandwidth.

---

### Post by Vaphell on 2009-02-26
do you have limits set in your transmission config? Maybe your pc uses whole bandwith and opens millions of sockets using a lot of resources? Cap total number of sockets at let's say 200-300, upload bandwith at let's say 50% of your pipe. It should help if you haven't done that.

---

