---
title: "Kernel Upgrade -Ath9x Madwifi"
date: 2009-03-24
forum: General Help
---

### Post by bluestreek on 2009-03-24
Basically I have a laptop with 8.04 which has kernel version 2.6.24 (I think) and ath9x madwifi driver require 2.6.26?  I would just update it but I cannot access the internet in ubuntu because obviously the wifi doesn't work and wired is not possible.

I considered downloading 8.10 but the download is to large for me.  Is there anyway to download something and copy it over and a usb to update the kernel and get ath9x working?

Any help would be great.

---

### Post by blazemore on 2009-03-24
There are .deb packages here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.27/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.27/)

---

### Post by bluestreek on 2009-03-24
> **blazemore said:**
> There are .deb packages here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.27/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.27/)

What is a header and what is an image, which ones should I download?

Also thanks for your reply :)

---

### Post by blazemore on 2009-03-24
Download the header and image corresponding to your architecture.
If unsure, do the All option (larger download)
Install both debs. I don't think the order matters, but I always do image first and have never had a problem.

---

