---
title: "Simple LightDM does not update"
date: 2011-11-25
forum: Desktop Environments
---

### Post by rabideau on 2011-11-25
I have three different variants of Ubuntu 11.10 (Lubuntu, Xubuntu & Unity) installed.  When i attempt to use SimpleLightDM to change my login screens I get a message indicating success.  When I Log-out and back nothing has changed, it remains the "ugly" Ubuntu purple.:(  Rebooting does not help... uninstall/ reinstall of all greeter apps does not help... change directory privs to 0777 does not help.

Any ideas????  Am I the only person with this problem?

---

### Post by rabideau on 2011-11-25
Sorry for being dumb... but here's what worked for me.  In terminal place the following command

sudo apt-get -o Dpkg::Options::="--force-confnew" install --reinstall lightdm

Reboot the system and Voila!:popcorn:

---

