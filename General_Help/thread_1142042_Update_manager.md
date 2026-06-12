---
title: "Update manager"
date: 2009-04-28
forum: General Help
---

### Post by vikram_af on 2009-04-28
I usually start Update Manager by typing "update-manager" or "update-manager -d" at command prompt. What is difference between typing "update-manager" and "update-manager -d"?

---

### Post by codeseer on 2009-04-28
> **vikram_af said:**
> I usually start Update Manager by typing "update-manager" or "update-manager -d" at command prompt. What is difference between typing "update-manager" and "update-manager -d"?

You can usually add '--help' to commands to see what parameters do when added to them. In this case, it seems that adding '-d' checks for development releases (possibly unstable or buggy, but more current) of packages.

---

### Post by iaculallad on 2009-04-28
Issuing the command **update-manager** on the terminal will launch the Update Manager windows (GUI front-end of APT), while **update-manager -d** command will check if upgrading to the latest development release is possible on your Ubuntu version.

```
man update-manager
```

---

### Post by vikram_af on 2009-04-28
Thanks for your help guys!!!

---

