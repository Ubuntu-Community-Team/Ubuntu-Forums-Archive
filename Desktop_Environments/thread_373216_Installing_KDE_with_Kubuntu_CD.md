---
title: "Installing KDE with Kubuntu CD"
date: 2007-03-01
forum: Desktop Environments
---

### Post by xardas on 2007-03-01
I was wondering if I could install the KDE with the kubuntu cd that I've burned. I insert the cd but the synaptic manager doesn't detect it. Any help?

---

### Post by aysiu on 2007-03-01
You need the Alternate CD.

You can't add Kubuntu with the Desktop CD. The Desktop CD allows you run a live session and install Kubuntu. It does not allow you to add Kubuntu to an existing installation.

---

### Post by xardas on 2007-03-01
How would i install kde with the alternate CD?

---

### Post by aysiu on 2007-03-01
> **xardas said:**
> How would i install kde with the alternate CD?
By typing these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

