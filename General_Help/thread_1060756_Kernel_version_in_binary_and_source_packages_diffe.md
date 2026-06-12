---
title: "Kernel version in binary and source packages differs"
date: 2009-02-05
forum: General Help
---

### Post by bff7755a on 2009-02-05
Hello.

I want to recompile a kernel module, but I have a problem. My current kernel version is 2.6.27.11.

When I download a kernel source package and build a module (ipw2200.ko) modprobe tells me that this module has an incorrect format.

```
[ibm-t43][mutex]~/build> sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/kernel/drivers/net/wireless/ipw2200.ko): Invalid module format
```

In Makefile I found that EXTRAVERSION for this kernel is 10:

```
[ibm-t43][mutex]/usr/src/linux-source-2.6.27> cat Makefile | grep EXTRAVERSION
EXTRAVERSION = .10
```

Is there a reason? I've also tried to get sources from Ubuntu git tree, but has the same result.

Differene between modules:

```
[ibm-t43][mutex]~/backup> diff ok notok
1c1
< filename:       ipw2200.ko.ok
---
> filename:       ipw2200.ko
29,30c29,30
< depends:        ieee80211
< vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 
---
> depends:        
> vermagic:       2.6.27.10 SMP mod_unload modversions 586
```

Thank you.

---

### Post by jlebeau on 2009-02-09
Hi, 

I've in the same situation (same kernel, same issue), trying to rebuild the cdc-acm module.

The modinfo output is the same..

Hoping some one will notice this problem and help to resolve this (issue is not present in 8.04.1)

---

