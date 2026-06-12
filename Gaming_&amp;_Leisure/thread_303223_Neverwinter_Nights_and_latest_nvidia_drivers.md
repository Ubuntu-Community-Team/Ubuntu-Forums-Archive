---
title: "Neverwinter Nights and latest nvidia drivers"
date: 2006-11-19
forum: Gaming &amp; Leisure
---

### Post by glennric on 2006-11-19
I tried installing the latest Nvidia drivers (9629) and discovered that Neverwinter Nights would then crash the xserver.  I don't know how to diagnose the problem.  After running Neverwinter I am dropped to the console and then the xserver restarts and I am taken back to the login screen.  I tried installing the nvidia drivers from the Nvidia site and from the amranth repositories.  I got the same result from both.  If I install the nvidia drivers from the Ubuntu Edgy repositories Neverwinter works fine.

---

### Post by Perfect Storm on 2006-11-20
Try check the nwn/logs, there's a nwclientError1.txt and a nwclientLog1.txt

---

### Post by leech on 2006-11-20
It's working here (I think I even had it running with Beryl with the 9625 beta drivers as well, though for some reason Beryl is acting funky with me right now, so can't test with the 9629)

We'll have to check your logs.

Leech

---

### Post by glennric on 2006-11-20
The plot thickens.  With the 9629 NVidia drivers installed, I ran Neverwinter and then I looked at the logs in ~/nwn/logs.  The result was that both were empty files.

---

