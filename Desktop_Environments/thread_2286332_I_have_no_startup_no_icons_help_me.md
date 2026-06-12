---
title: "I have no startup no icons help me"
date: 2015-07-11
forum: Desktop Environments
---

### Post by ales4 on 2015-07-11
I install kwin on ubuntu and when I reboot my computer my startup icons was gone I can open only with ctrl+alt+f1 or f2 I try with command sudo ppa-purge ppa:gnome3-team/gnome3 and then an error sudo ppa-purge : command not found can someone help me I can't find nothing on internet to resolve this problem   thank you

---

### Post by oldos2er on 2015-07-11
ppa-purge isn't installed by default, but you can install it with ```
sudo apt-get update && sudo apt-get install ppa-purge
``` I'm a little perplexed by your problem though, I wouldn't expect kwin to be in the gnome3-team PPA. Also not sure what "startup icons" refers to. Which version of Ubuntu are you running?

---

