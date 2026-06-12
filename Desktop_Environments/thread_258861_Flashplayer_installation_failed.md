---
title: "Flashplayer installation failed"
date: 2006-09-16
forum: Desktop Environments
---

### Post by ttry72 on 2006-09-16
Hi All
I did the Flash player installation without success. 

It says that packet is already installed and the depencies were ok. It is the latest version.

FIREFOX_DSP="aoss" were done.

How shame, five potential users are waiting this feature :( 

Is there anyone who can help me, please?

---

### Post by Super J on 2006-09-16
I was having trouble with flash as well. I installed it via Automatix, but when I went to youtube it said it wasn't installed. Try this:
```
mkdir ~/mozilla/plugins
```
Then go to a site that uses flash, youtube for example, and install it via Firefox. That fixed it for me.

---

### Post by jtbl on 2006-09-16
There is a bug in the package in the Ubuntu repos.  This bug was caused by Adobe releasing version 7.0.68 a few days ago.  This bug did get fixed in the Flash Plugin option in Automatix 6.5-3.

---

### Post by ttry72 on 2006-09-24
> **jtbl said:**
> There is a bug in the package in the Ubuntu repos.  This bug was caused by Adobe releasing version 7.0.68 a few days ago.  This bug did get fixed in the Flash Plugin option in Automatix 6.5-3.

Thanks. I installed by manually and it works now very well. :)

---

