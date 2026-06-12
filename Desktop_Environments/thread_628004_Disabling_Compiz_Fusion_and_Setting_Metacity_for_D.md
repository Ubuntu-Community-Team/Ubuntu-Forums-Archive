---
title: "Disabling Compiz Fusion and Setting Metacity for Default"
date: 2007-11-30
forum: Desktop Environments
---

### Post by Theosa on 2007-11-30
How can I disable compiz fusion totally and revert back to metacity? I mean by removing compiz and related packages. Any help will be appreciated.

---

### Post by Happy_Man on 2007-11-30
Try this command (make sure Metacity is running first!)

```
sudo apt-get remove compiz compiz-core compiz-fusion-plugins-* compiz-gnome
```

---

