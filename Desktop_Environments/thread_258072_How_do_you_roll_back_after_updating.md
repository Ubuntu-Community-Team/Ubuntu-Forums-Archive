---
title: "How do you roll back after updating?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by linuxNewb on 2006-09-15
My internet has been down all morning after updating the kernel, linux-restricted-modules, and linux-restricted-helperscript.

I will only have access to this box for another half-hour. Can someone please tell me how to roolback those 3 things. I tried booting with the old kernel version, but when I did, my wireless didn't work at all, now it at least connects to my wireless router (even though I can't even ping it).

How can I rollback the kernel and the two restricted packages. Thank you in advance.

---

### Post by lamego on 2006-09-15
Those older verions may be at
/var/cache/apt/archives
You can install them manually with:
```
sudo dpkg -i package_name
```

---

### Post by juraj on 2006-09-15
You should try the option "Force version" in Synaptic, that will allow you to override the default (latest) version of the package.

---

