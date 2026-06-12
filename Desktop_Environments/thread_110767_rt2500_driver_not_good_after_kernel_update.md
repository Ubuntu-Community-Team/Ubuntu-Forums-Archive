---
title: "rt2500 driver not good after kernel update?"
date: 2005-12-31
forum: Desktop Environments
---

### Post by crispibits on 2005-12-31
Has anyone else seen a drop in performance from the rt2500 wireless driver after the last kernel update (to 2.6.10-12-386)?  I was getting poor signal quality and often dropped the connection.

I thought that it might have been the fairy lights on the tree (honestly), but experimenting showed this not to be the case.  I then downloaded and compiled up the latest CVS rt2500 driver, and all is well again.

Anyone else finding this?  If so I'll raise a bug...

---

### Post by zoiks on 2005-12-31
My experience has been (lately, but can't tell if it's after the kernel upgrade) that rt2500 loses the connection frequently.  I haven't re-compiled the rt2500 module, but I *have* compiled and installed the RaConfig2500 utility.  It seems when I start up the utility, without having to change settings or anything, the connection just comes back and stays on.  Go figure.

---

