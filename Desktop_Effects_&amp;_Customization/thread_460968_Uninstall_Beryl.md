---
title: "Uninstall Beryl?"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by orange2k on 2007-06-01
Well it runs just fine, but its nothing more than eyecandy and it does provoke problems in certain situations, so Ive decided to uninstall it and simply enable the default desktop effects when I like.

What command do I have to run to uninstall it?

---

### Post by Ub1476 on 2007-06-01
```
sudo aptitude remove beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

---

### Post by original2k on 2007-06-01
you could "mark uninstall" the components from the synaptic package manager as well, that's how i did it at least

---

