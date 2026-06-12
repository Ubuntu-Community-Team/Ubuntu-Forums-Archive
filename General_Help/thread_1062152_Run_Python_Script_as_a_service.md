---
title: "Run Python Script as a service"
date: 2009-02-06
forum: General Help
---

### Post by supanatral on 2009-02-06
I created a ubuntu server which allows me to run a windows setup using PXE so I don't need a cd. The issue is that it needs me to run a python script that detects the clients network card. Is there a way to set this up using a background service?

---

### Post by mb_webguy on 2009-02-06
Add it to the /etc/init.d/local/rc.local file (which you'll probably have to create).  [Here]("https://help.ubuntu.com/community/RcLocalHowto")'s some more info.

---

### Post by supanatral on 2009-02-09
Thank you. Now, you should know that this script needs to always be running. it waits there running until a client boots off of pxe and it detects the network card drivers. will that still work?

When I do that heres the error I get:
> Could not load start as cache, build it with infparser.py

However, I can run it normally and I already built it with infparser.py

---

