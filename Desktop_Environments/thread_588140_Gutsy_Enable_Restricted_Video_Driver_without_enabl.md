---
title: "Gutsy Enable Restricted Video Driver without enabling Compiz?"
date: 2007-10-23
forum: Desktop Environments
---

### Post by radioraheem on 2007-10-23
I have a system with onboard dual-head video that uses a nvidia chipset (one DVI and one analog connection).  The last time I tried to install Gutsy on it I had to start all over again with Feisty due to the way restricted video drivers and compiz are handled.

Basically my problem is the onboard nvidia doesn't seem to have enough juice to run compiz on 2 screens @ 1680x1050.  The screens won't run at their correct resolution without the restricted driver, but as soon as I enable it Gutsy tries to enable compiz and all hell breaks loose (read:  unusable desktop).

The problem seems to be that Gutsy is enabling compiz as soon as the restricted driver is enabled, without ever asking you if you actually want compiz turned on.

All I want is a working desktop without effects.  Searching the forums hasn't provided me with much info so far.

Anyone have any ideas/suggestion?  Thanks in advance.

---

### Post by brk3 on 2007-10-23
I enabled the nvidia driver on my system and then had to enable compiz seperatly so this is a strange one.. if you're really stuck and don't want to use compiz you could just uninstall it? That would stop it from starting when you try to enable the driver.  Maybe someone will have a better solution though..

---

