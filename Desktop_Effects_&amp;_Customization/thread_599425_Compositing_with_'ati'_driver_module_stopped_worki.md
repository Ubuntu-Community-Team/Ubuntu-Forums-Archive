---
title: "Compositing with 'ati' driver module stopped working"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by matthias_k on 2007-11-01
Hi,

after installing Gutsy, compositing with the open source ati driver worked just fine. Nevertheless I installed the fglrx driver to see the difference in performance, but I had to install Xgl for that. The fglrx driver turned out to break completely on me, so I simply switched back to 'ati' in xorg.conf, but now compositing doesn't work anymore:

> 
matthias:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e48 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

I don't even get what's the error message is here. That Xgl is missing? Of course it's missing, I don't need it anymore.

Any idea?

---

### Post by matthias_k on 2007-11-01
bump

---

### Post by Forlong on 2007-11-01
Do you still have fglrx installed? If so, remove the driver again:
```
sudo apt-get remove xorg-driver-fglrx
```

---

### Post by matthias_k on 2007-11-01
> **Forlong said:**
> Do you still have fglrx installed? If so, remove the driver again:
```
sudo apt-get remove xorg-driver-fglrx
```

Hey cool, deinstalling the fglrx driver did the job. Thanks!

I don't get why this is necessary though, but thanks.

---

