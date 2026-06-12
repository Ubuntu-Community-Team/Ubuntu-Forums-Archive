---
title: "update behind proxy"
date: 2009-04-20
forum: General Help
---

### Post by eworman on 2009-04-20
Hi there,

This is a problem discussed a couple of time in other threads, but I can find a solving for my case.

I am behind university automatic proxy and I was bothered by the problem of updating. The http proxy is stored in a file XXXX.pac. Without export it into .bashrc I have 403 error which means basically I am not able to download the list file from server if I try sodo apt-get update. After I added a line of export http_proxy="location/XXXX.pac" and retry sodu apt-get update again, I have 404 error which means the server can not find the file I was asking. However, in both case, if I put the link to thos list files into firefox, I have no problem to retrieve them. I think it is something to do with configuration of wget, but I dont' know what I should do exactly.


On the other hand, synaptic. I can make synaptic work by manually put proxy information, say address and port, which I get from XXXX.pac into network options of synaptic. That really works, but nothing change for apt-get.


Can anyone give me some hint?

Best regards.

---

