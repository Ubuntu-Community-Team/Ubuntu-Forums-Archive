---
title: "Desktop Effects won't work!"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by zlegge08638 on 2007-12-08
I go to Desktop Effects and then a window pops up saying "Composite extension is not available".  I also have Beryl and an ATI accelerated Radeon Graphics card, whats wrong?

---

### Post by Ub1476 on 2007-12-08
If you are running Ubuntu 7.10 you don't need Beryl. To fix your problem you need to install XGL. Search for it in Synaptic or type into terminal:

```
sudo apt-get install xserver-xgl
```

Then logout and login again.

---

### Post by zlegge08638 on 2007-12-08
Actually I have Ubuntu 7.04 but I did the XGL thing and I still get the Composite Extension isn't available, what does that mean?

---

### Post by Ub1476 on 2007-12-08
If you are using Feisty, see how to set up XGL [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_Beryl_using_proprietary_FGLRX_drivers_from_ATI").

It says so because you are running the restricted ati drivers, which do not support AIGXL (default session which you are using now).

ATI has released AIGXL supported drivers now though, but they are very unstable at the moment. When Hardy Heron comes (April), it will probably work out of the box for all ATI cards:)

---

