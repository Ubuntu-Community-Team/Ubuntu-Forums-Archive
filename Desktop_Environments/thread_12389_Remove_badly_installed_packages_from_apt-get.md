---
title: "Remove badly installed packages from apt-get"
date: 2005-01-24
forum: Desktop Environments
---

### Post by lykoszine on 2005-01-24
Hiya

I tried install something with apt-get (mldonkey-server) which has an install script. Something I did in the config causes this script to crash, so it won't install.

Now it tries to install it everytime I run apt-get, but won't remove it with apt-get remove because it is not installed.

How can I get rid of it? Cheers

---

### Post by lykoszine on 2005-01-24
[QUOTE=lykoszine]Hiya

I tried install something with apt-get (mldonkey-server) which has an install script. Something I did in the config causes this script to crash, so it won't install.

Now it tries to install it everytime I run apt-get, but won't remove it with apt-get remove because it is not installed.

How can I get rid of it? Cheers[/QUOTE]
 Managed to do it through synaptic. Still not sure how to do it from CLI though...

---

### Post by SFN on 2005-01-24
```
sudo apt-get remove --purge mldonkey-server
```

---

