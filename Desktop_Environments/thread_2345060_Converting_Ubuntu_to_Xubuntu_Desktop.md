---
title: "Converting Ubuntu to Xubuntu Desktop?"
date: 2016-11-30
forum: Desktop Environments
---

### Post by yodayams on 2016-11-30
I have Ubuntu 16.04 LTS installed, but I want to use the Xubuntu Desktop. I read to install package xubuntu-desktop, but when I try this I get an error:

sudo apt-get install xubuntu-desktop
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can someone please help me?

---

### Post by howefield on 2016-11-30
Generally mean that you have more than one application simultaneously trying to use apt. Close all package managers, eg Software Centre, Synaptic and try again.

---

### Post by yodayams on 2016-11-30
Thanks that worked!

---

