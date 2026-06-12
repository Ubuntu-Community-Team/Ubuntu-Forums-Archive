---
title: "Ati Driver on Ubuntu 16.04"
date: 2016-08-25
forum: Desktop Environments
---

### Post by melhorhos on 2016-08-25
Hi , i have a Arcade maked in Ubuntu 15 , have a Ati Radeon that work nice in Ubuntu 15 with fglrx , but in the Ubuntu 16 , it not appear in the propietary drivers , is there a way to install fglrx in ubuntu 16.04 ? 


Thank You Very Much

---

### Post by Bashing-om on 2016-08-25
melhorhos; Hello;

Short answer is no. there is no FGLRX (proprietary) driver for 16.04's release. AMD is throwing  full support to open source for us.
What card do you have ?
```

lspci -vnn | grep VGA -A 12

```

If this is a later edition card, maybe there is a beta driver for testing available ??

[INDENT][INDENT]the times
[INDENT][INDENT][INDENT]they are achange'n
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2016-08-25
No.  fglrx cannot be installed in 16.04.  fglrx is not compatible with the version of X Server in 16.04.

When 16.04 is installed, the intstaller will use either the open source Radeon driver or the open source AMDGPU driver.  The latter only applies to a limited number of GPU chipsets at the moment.

---

