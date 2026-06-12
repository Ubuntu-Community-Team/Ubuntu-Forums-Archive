---
title: "Need Help Updating Kernel Cmdline on Ubuntu 24.04.1 with FDE and TPM Integration"
date: 2024-11-06
forum: Desktop Environments
---

### Post by inckiekage on 2024-11-06
I'm currently running Ubuntu 24.04.1 with Full Disk Encryption (FDE) and TPM integration. I’m looking to update the kernel cmdline to try to work around an issue with Intel i915 that’s causing screen freezing and flickering. 

Relevant bug reports for reference:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062951](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062951)
[https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049027](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049027)

To resolve this, I tried adding *intel_iommu=igfx_off* to the cmdline with these commands:

```

$ sudo snap set system system.kernel.dangerous-cmdline-append="intel_iommu=igfx_off"
$ sudo snap get system system.kernel.dangerous-cmdline-append
intel_iommu=igfx_off

```

After rebooting, however, the cmdline doesn’t show the parameter as expected:

```

$ cat /proc/cmdline 
snapd_recovery_mode=run console=ttyS0,115200n8 console=tty1 panic=-1 quiet splash

```

---

