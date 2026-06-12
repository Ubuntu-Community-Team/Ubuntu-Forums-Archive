---
title: "Unable to install or update in Ubuntu 10.10"
date: 2010-11-28
forum: Desktop Environments
---

### Post by Bolodan on 2010-11-28
When I go to install anything, whether it's through the Ubuntu Software Centre, a downloaded .deb file, or even using the update manager. I always get an error installing. Is there any possible solution to be able to update my system, or install programs.

---

### Post by tom4everitt on 2010-11-29
Try running
```

sudo dpkg-reconfigure -a
sudo apt-get --fix-broken
sudo apt-get update
sudo apt-get upgrade

```
in a terminal. 

If it works: fine! Otherwise tell us what error messages you get.

---

