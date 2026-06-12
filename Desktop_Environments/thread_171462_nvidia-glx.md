---
title: "nvidia-glx"
date: 2006-05-06
forum: Desktop Environments
---

### Post by nami on 2006-05-06
Hi

How do I find out if nvidia-glx is installed on my system?

nami

---

### Post by kmartinson on 2006-05-06
Wouldn't it say somewhere (maybe under the devices section) in xorg.conf (/etc/X11/xorg.conf)?  Just guessing here....

Also, keep in mind I'm an ATI user - but if you didn't actually install nvidia-glx then I don't think you have it.

sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable$ sudo apt-get install
nvidia-glx-config enable

Good luck.

---

