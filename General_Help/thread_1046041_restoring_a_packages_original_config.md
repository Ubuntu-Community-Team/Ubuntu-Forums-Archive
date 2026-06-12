---
title: "restoring a packages original config"
date: 2009-01-21
forum: General Help
---

### Post by LonelyStar on 2009-01-21
Hi,

I sometimes come to the situation, that I would like to restore the configuration of a package to its original state (to the same as when it was installed). Reinstalling the package does not help.

How do I do that?

THanks!
Nathan

---

### Post by dcstar on 2009-01-21
> **LonelyStar said:**
> Hi,

I sometimes come to the situation, that I would like to restore the configuration of a package to its original state (to the same as when it was installed). Reinstalling the package does not help.

How do I do that?

THanks!
Nathan

Use Synaptic to completely remove the package, then install.

---

### Post by bikeboy on 2009-01-21
Hi,

You need to purge the package before re-installing it. Purging removes the configuration.

```
sudo apt-get --purge remove <package> && sudo apt-get install <package>
```

---

