---
title: "Sotware Update stuck"
date: 2012-10-23
forum: Desktop Environments
---

### Post by Tex-Twil on 2012-10-23
Hi,
quite often when I update my packages using the Software Update, the installation does not finish and stays stuck at "Running dpkg ..."

[IMG]http://f.cl.ly/items/2L3F1t0B1h1A112I0d17/dpkg.png[/IMG]

What shall I do in this case? Just close the installer?

cheers

---

### Post by kc1di on 2012-10-23
close the install then go to a terminal and do the following
one command at a time.

```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get upgrade

```
post any error codes you get.

---

