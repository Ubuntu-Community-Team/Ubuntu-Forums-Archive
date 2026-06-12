---
title: "synaptic"
date: 2011-06-26
forum: Desktop Environments
---

### Post by robeec on 2011-06-26
hi, i cannot get synaptic to run. i get 'dpkg was interrupted. you must manually run 'sudo dkpg-configure-a' to correct the problem. i type that exactly into the terminal but nothing after i give my pw.
any ideas?
thanks!

---

### Post by nzjethro on 2011-06-26
Run

```
sudo dkpg-configure-a && sudo apt-get -f install
```

Then try again to reinstall whatever package it was through synaptic.

---

### Post by oldos2er on 2011-06-27
The correct command is ```
sudo dpkg --configure -a
```

---

