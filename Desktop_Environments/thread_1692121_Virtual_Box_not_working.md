---
title: "Virtual Box not working"
date: 2011-02-20
forum: Desktop Environments
---

### Post by MechaMechanism on 2011-02-20
Creating the virtual machine works.  But when I try to turn on the machine I get an error.  This is the first time I installed it.

Ubuntu 10.04.2

Error message.
p, li { white-space: pre-wrap; } Failed to open a session for the virtual machine natty.
 VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).

---

### Post by An Sanct on 2011-02-21
VirtualBox cannot work on a kernel, that already has a different virtualisation layer (KVM).

This is a well known issue, the solution is to uninstall KVM or not use VirtualBox.

```
sudo rmmod kvm-[cpu architecture]
```

[more info]("https://help.ubuntu.com/community/KVM/FAQ")

PS. As it is a known issue, please google for additional answers, before doing that.

---

### Post by MechaMechanism on 2011-02-21
I uninstalled KVM from synaptic and it works now.  Thanks An Sanct.

---

