---
title: "Unity Compiz Plugin out after kernel update"
date: 2011-11-21
forum: Desktop Environments
---

### Post by BC59 on 2011-11-21
A couple of hours ago I updated to kernel 3.0.0.0-13 and after the reboot, the Unity plugin on Compiz Config was unchecked and the Unity launcher lost the tweaks made.
Trying to check the plugin I have the error message 

> Some key and edge bindings of Plugin Ubuntu Unity Plugin conflict with other plugins. Do you want to resolve these conflicts? IGNORE OR RESOLVE

Asking to Resolve pushing every options there is no solution.

I already reset Unity and Compiz. Compiz reset gives me the same error.

Any ideas?

---

### Post by BC59 on 2011-11-21
Booting using the previous kernel 3.0.0.0-12 everything works perfectly.

---

### Post by BC59 on 2011-11-21
Finally I realized that I'm using now Unity 2D. This only happens using the new kernel.

I filled a bug report in Launchpad.

The bug is called Bug #893322
"Unity Compiz Plugin off after kernel update"

If you have a similar problem please subscribe to the bug.

---

### Post by BC59 on 2011-11-22
A workaround is to reinstall the proprietary video drivers.

---

### Post by BC59 on 2011-11-22
According to Ubuntu 11.10 (Oneiric Ocelot) guide

> Sometimes after a kernel upgrade a proprietary driver may stop working. In such a case, try installing the new linux-headers that match the newly upgraded kernel:

```
sudo apt-get install linux-headers-$(uname -r)
```

> If dkms and build-essential have never been installed on your system, these can also be worthwhile:

```
sudo apt-get install dkms build-essential
```

---

