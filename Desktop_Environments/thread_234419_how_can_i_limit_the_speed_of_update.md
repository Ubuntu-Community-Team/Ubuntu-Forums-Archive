---
title: "how can i limit the speed of update"
date: 2006-08-11
forum: Desktop Environments
---

### Post by mfarouk30 on 2006-08-11
hello

i want to limit the speed that apt use to download programs and updates

---

### Post by ciscosurfer on 2006-08-11
Can you tell me why you want to do this?  Usually, grabbing updates from apt at the fastest speed possible is desired.

However, it's completely possible to do what you want:

First, enable your "universe" repository.

You can use wondershaper to "shape" the download/upload speed of your connections -- it's an easy to use traffic shaping script.```
sudo aptitude update && sudo aptitude install wondershaper
```And you can also take a look [at this page]("http://www.lartc.org/lartc.html#LARTC.IPROUTE2"), the iproute2 section.

---

