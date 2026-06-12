---
title: "ATI-Compiz on Gutsy"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by agiamba on 2007-11-18
Hi,

I have an ATI Mobility x300. On Feisty I had two log-in sessions, Gnome with XGL and Gnome without, so I could use Beryl on one, and still be able to play games with hardware-acceleration on the other game. I wiped the installation and did a fresh install of Gutsy because when I upgraded it messed a few things up, and both logins had XGL enabled for some reason.

Anyone know if I can still do this in Gutsy? I have hardware-acceleration enabled right now, so Compiz isn't working.

---

### Post by Forlong on 2007-11-18
Install Xgl
```
sudo apt-get install xserver-xgl
``` and read the lightbulb-message carefully.

---

### Post by agiamba on 2007-11-18
wont XGL stop my hardware acceleration?

---

### Post by Forlong on 2007-11-19
> **Forlong said:**
> read the lightbulb-message carefully.
It will tell you how to disable Xgl for a session.

---

