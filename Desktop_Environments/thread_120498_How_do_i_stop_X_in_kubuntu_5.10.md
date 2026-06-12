---
title: "How do i stop X in kubuntu 5.10?"
date: 2006-01-22
forum: Desktop Environments
---

### Post by solarwind on 2006-01-22
Hi. How do i stop X in kubuntu 5.10? I am trying to install an Nvidia driver for my graphics card which requires me to first stop X.

How do i stop X in kubuntu 5.10?

All help is much appreciated. 
Thankyou.

---

### Post by heimo on 2006-01-22
On terminal:
```
sudo /etc/init.d/kdm stop

```
to stop X, and:

```
sudo /etc/init.d/kdm start

```
to start it again.

---

