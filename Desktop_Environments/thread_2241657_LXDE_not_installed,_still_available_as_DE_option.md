---
title: "LXDE not installed, still available as DE option?"
date: 2014-08-27
forum: Desktop Environments
---

### Post by leepe on 2014-08-27
Hello,

I booted up by Ubuntu pc for the first time in a couple months the other day, and noticed that LXDE was installed. I wanted to get rid of it, so I opened up a terminal and punched in ```
sudo apt-get remove lxde
```
but the command returned that lxde was not installed. For good measure, I also tried ```
sudo apt-get remove lubuntu-desktop
``` but the command returned that that wasn't installed either. I tried running apt-get update and then apt-get upgrade, then trying commands above again, but still the same message. I know LXDE is installed because its available as an option when get to the login screen. I can boot into LXDE and it works fine. I'm on 14.04 LTS. What's going on?

---

### Post by BazBear on 2014-08-27
Odd. Did you try removing it using Synaptic?

---

### Post by leepe on 2014-08-27
Not yet. Would that make a difference?

---

### Post by BazBear on 2014-08-27
Maybe not. I just looked through my Synaptic list, and the LXDE meta package isn't installed on this machine either, even though it's originally a Lubuntu installation, and LXDE is the only DE I have on here at the moment. I (apparently) have all the LX packages that go with it though (LXpanel, LXtask, etc. etc.).

---

### Post by leepe on 2014-08-27
Hmm. I don't think mine is lubuntu originally. I checked the version with a command I found the other day and it returned ubuntu. I'll try with synaptic when i get back, and I'll post back with results.

---

### Post by sisco311 on 2014-08-27
lxde and lubuntu-desktop are metapackages. Removing them will not remove their dependencies. 

Which version/flavour of Ubuntu are you using and how did you install lxde?

---

### Post by BazBear on 2014-08-27
> **sisco311 said:**
> lxde and lubuntu-desktop are metapackages. Removing them will not remove their dependencies. 

Which version/flavour of Ubuntu are you using and how did you install lxde?
Ah, Lubuntu-core is the meta package on my instalation, thanks for pointing this out. Not that I plan to uninstall it, but this may help romain_astie2, so thanks!

---

### Post by leepe on 2014-08-27
still stuck!
apparently lubuntu-core is not installed. I'm using ubuntu 14.04. Not lubuntu, just ubuntu as far as i can remember. I installed lxde through just a standard apt-get command. So confused!

---

### Post by leepe on 2014-08-27
doesn't matter. I'm reinstalling with xubuntu right now, as xfce is my DE of choice anyway. thanks for the support!

---

