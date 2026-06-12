---
title: "Error Message - can't access Synaptic Package Manager"
date: 2007-12-18
forum: Desktop Environments
---

### Post by Gmonster on 2007-12-18
Hi,

The error says:

"AN ERROR OCCURED, the following details are provided: E: dpkg was interrupted, you must mannually correct the problem. E:_cache->open()failed, please report."

How do I correct this problem?  This error is preventing me from access Synaptic Package Manager and also the Add/Remove files.  I'm also unable to access the Update Manager, which means I can't keep up with the updates.

Please advise.

---

### Post by taurus on 2007-12-18
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Gmonster on 2007-12-18
Hi, I followed your instructions and I got the same error messsage.  Please see the two screenshots I posted here:

[http://docs.google.com/Doc?id=dfn2xdf3_10fvbq5npb](http://docs.google.com/Doc?id=dfn2xdf3_10fvbq5npb)

Make sure you scroll down to see the second screenshot where it shows the error...

Please advise.

---

### Post by taurus on 2007-12-18
```
sudo dpkg --**configure** -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Gmonster on 2007-12-18
Okay, thanks, I ran it correctly this time, and here is a screenshot of what came up:


[http://docs.google.com/Doc?id=dfn2xdf3_10fvbq5npb](http://docs.google.com/Doc?id=dfn2xdf3_10fvbq5npb)

---

