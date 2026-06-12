---
title: "Can't insert new kernel module"
date: 2009-03-07
forum: General Help
---

### Post by jb64 on 2009-03-07
I have built compat-wireless (basically all linux wireless drivers).  Afterwards I tried making a new folder called "ath5k" in /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless, where I copied ath5k.ko to. However "modprobe ath5k" will give me a "FATAL: module not found" message.  Any help?

PS I do not want to use "make modules_install".

---

### Post by sdennie on 2009-03-07
Before inserting the module, try running:

```

sudo depmod -a

```

That will rebuild some tables that define the available modules.

---

### Post by jb64 on 2009-03-07
It still doesn't find the module...

Edit: And this won't work either?

```

sudo modprobe '/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/ath5k/ath5k.ko'
FATAL: Module /lib/modules/2.6.27_7_generic/kernel/drivers/net/wireless/ath5k/ath5k.ko not found.

```

---

