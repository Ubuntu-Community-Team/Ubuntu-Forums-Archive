---
title: "VPN installation instructions ask for kernel source that I can't locate"
date: 2006-01-06
forum: Desktop Environments
---

### Post by will103 on 2006-01-06
Hi,

I am running Ubuntu 5.10 on X86 hardware. My work has asked me to install a VPN client on my home machine so that I can access restricted services - normally only available from within their network. The installation instructions state that I should download the source files for the kernel that I currently run, which is 2.6.10-12. However I cannot find those source files in the Ubuntu repositries. Would it be possible to use the plain kernel source from 

[http://www.kernel.org/](http://www.kernel.org/) ?

I am concerned that the kernel I am running on Ubuntu is probably patched specifically for the distribution.

Thanks in advance

Will103

---

### Post by timfrost on 2006-01-06
If your corporate VPN is Cisco, then you should install the VPNC package, and set it up.
```

$ apt-cache search vpnc
vpnc - Cisco-compatible VPN client
sudo apt-get  install vpnc
sudo nano /etc/vpnc/example.conf

```
Note: you need to code the real group shared password in vpnc configuration. not the encrypted versin that cisco use.

If the VPN isn't Cisco, you will need to install enough development tools to compile a kernel module.

Try the following:
```

sudo apt-get install build-essential linux-headers-$(uiname -r) gcc-3.4 g++-3.4

```

NOTE:  You will need to set CC=gcc-3.4 to build the kernel driver for breezy, because:
* GCC 3.4 was used to build the breezy kernel
* GCC 4.x is the default compiler version for apps in breezy

---

### Post by will103 on 2006-01-09
[QUOTE=timfrost]If your corporate VPN is Cisco, then you should install the VPNC package, and set it up.
```

$ apt-cache search vpnc
vpnc - Cisco-compatible VPN client
sudo apt-get  install vpnc
sudo nano /etc/vpnc/example.conf

```
Note: you need to code the real group shared password in vpnc configuration. not the encrypted versin that cisco use.

If the VPN isn't Cisco, you will need to install enough development tools to compile a kernel module.

Try the following:
```

sudo apt-get install build-essential linux-headers-$(uiname -r) gcc-3.4 g++-3.4

```

NOTE:  You will need to set CC=gcc-3.4 to build the kernel driver for breezy, because:
* GCC 3.4 was used to build the breezy kernel
* GCC 4.x is the default compiler version for apps in breezy[/QUOTE]

Thanks for your help Timfrost,

I managed to get the VPN software installed.

Will103

---

