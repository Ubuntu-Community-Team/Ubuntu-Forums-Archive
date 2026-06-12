---
title: "wireless problems after ubuntu 11.04 install"
date: 2011-12-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rebeccabatchelder on 2011-12-02
ok, I have read a million of these threads, and i know that apparently anyone dumb enough to own a dell computer (like me) has issues with their wireless connection after installing new versions of ubuntu. i fixed the issue when i installed ubuntu 10, but i recently upgraded to 11 and I can't seem to resolve the issue this time. here's what i've got: 
Dell Inspiron 1501
 Network controller [0280]: Broadcom Corporation BCM4311

i already check this page
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
and installed the sta driver and activated it, which didn't seem to resolve the issue, so then i installed the b43 driver, but i couldn't activate it, because it didn't show up under my additional drivers, so now i'm at a loss.

and i pretty much don't know anything about ubuntu, so speak slowly. i can't even seem to find the synaptic package manager any more. thanks in advance to anyone who offers me help!

---

### Post by NickCarriere on 2011-12-02
> **rebeccabatchelder said:**
> ok, I have read a million of these threads, and i know that apparently anyone dumb enough to own a dell computer (like me) has issues with their wireless connection after installing new versions of ubuntu. i fixed the issue when i installed ubuntu 10, but i recently upgraded to 11 and I can't seem to resolve the issue this time. here's what i've got: 
Dell Inspiron 1501
 Network controller [0280]: Broadcom Corporation BCM4311

i already check this page
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
and installed the sta driver and activated it, which didn't seem to resolve the issue, so then i installed the b43 driver, but i couldn't activate it, because it didn't show up under my additional drivers, so now i'm at a loss.

and i pretty much don't know anything about ubuntu, so speak slowly. i can't even seem to find the synaptic package manager any more. thanks in advance to anyone who offers me help!

I had an issue with my wireless USB drive before my clean install of 11.04 and this is what helped me:

[http://en.wikipedia.org/wiki/NDISwrapper]("http://en.wikipedia.org/wiki/NDISwrapper")

also look at this, might help:

[http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working]("http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working")

With NDISwrapper you might need to do your research and find the windows drivers.

---

