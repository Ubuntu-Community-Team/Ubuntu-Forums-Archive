---
title: "&quot;Failed to fetch&quot; error"
date: 2009-04-01
forum: General Help
---

### Post by DannoXD on 2009-04-01
I've looked around on countless websites for anything pertaining to this error but I've come up null, so hopefully someone here might have a clue what this means.

---------------------------------
Failed to fetch [http://ppa.launchpad.net/gkulyk/ubuntu/dists/intrepid/mai/source/Sources.gz](http://ppa.launchpad.net/gkulyk/ubuntu/dists/intrepid/mai/source/Sources.gz)  404 Not Found
---------------------------------

I've read on other websites that I need a key for the ppa but the walkthroughs don't meet this address.

---

### Post by plucky on 2009-04-01
> **DannoXD said:**
> I've looked around on countless websites for anything pertaining to this error but I've come up null, so hopefully someone here might have a clue what this means.

---------------------------------
Failed to fetch [http://ppa.launchpad.net/gkulyk/ubuntu/dists/intrepid/mai/source/Sources.gz](http://ppa.launchpad.net/gkulyk/ubuntu/dists/intrepid/mai/source/Sources.gz)  404 Not Found
---------------------------------

I've read on other websites that I need a key for the ppa but the walkthroughs don't meet this address.


The closest address I could find on that repository is  [http://ppa.launchpad.net/gkulyk/ubuntu/dists/intrepid/main/source/Sources.gz](http://ppa.launchpad.net/gkulyk/ubuntu/dists/intrepid/main/source/Sources.gz)

There is an n missing in main.Edit your sources list and then update.


Good Luck

---

### Post by DannoXD on 2009-04-01
I added the "n" and now I am receiving the error of 

--------------
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DBF1CA1622460E60
--------------

---

### Post by plucky on 2009-04-01
This [thread]1056099[/thread] might help or this [Launchpad Blog](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu) will show you how to add the PPA key.


Good Luck

---

### Post by DannoXD on 2009-04-01
Thanks a bunch, all fixed.

---

