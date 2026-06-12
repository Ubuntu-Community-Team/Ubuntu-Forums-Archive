---
title: "Jaunty 9.04 Final - Which NVIDIA 180 version is included?"
date: 2009-04-21
forum: General Help
---

### Post by dt_ on 2009-04-21
Hello,

Quick question. The latest version of the Nvidia 180 drivers for Linux is 180.44. Is this version the one that is available in the System -> Administration -> Hardware Drivers menu in Jaunty (the final version that comes out in two days)? Or at least, in the RC? From what I understand this version fixes some bugs present in earlier 180.xx versions.  Thanks! :)

**edit:** Actually, it looks like they just released a new version today (180.51).  Is THAT version in 9.04? :D

---

### Post by Yellow Pasque on 2009-04-21
[http://packages.ubuntu.com/jaunty/nvidia-180-kernel-source](http://packages.ubuntu.com/jaunty/nvidia-180-kernel-source)

---

### Post by dt_ on 2009-04-21
Fair enough. But does that mean that this is the version actually pre-installed on the OS? Or just the most recent version of the drivers available in the package repository?
Thanks!

---

### Post by Yellow Pasque on 2009-04-21
Restricted drivers aren't pre-installed. The LiveCD will use the "nv" driver. If you use Ubuntu's method of installing restricted drivers (i.e. Jockey), you will get whatever version is currently in the restricted repo (shown by the link in the last post). If you want something newer, you'll need to install it yourself or use a tool like Envy.

---

### Post by FredB on 2009-04-22
And there will be buggy drivers - or am I wrong - for some nvidia hardware, like GeForce 7000M which only give black screen. I have to use nvidia 173 driver on my jaunty since alpha4 days.

---

### Post by dcstar on 2009-04-22
> **FredB said:**
> And there will be buggy drivers - or am I wrong - for some nvidia hardware, like GeForce 7000M which only give black screen. I have to use nvidia 173 driver on my jaunty since alpha4 days.

The 9.04 Nvidia drivers install screen gives you a multitude of versions to install, with the latest at the top.

I would imagine that if a user has trouble it shouldn't be too difficult to remove the driver and then let the process repeat with them selecting a different one from the list.

---

### Post by FredB on 2009-04-23
> **dcstar said:**
> The 9.04 Nvidia drivers install screen gives you a multitude of versions to install, with the latest at the top.

I would imagine that if a user has trouble it shouldn't be too difficult to remove the driver and then let the process repeat with them selecting a different one from the list.

Of course. If this person knows how to boot in "fallback" mode and knows how to remove the *"buggy"* version ;)

---

