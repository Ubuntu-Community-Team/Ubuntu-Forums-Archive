---
title: "Install VIRTUAL MACHINE UBUNTU"
date: 2009-05-22
forum: General Help
---

### Post by luisridaocruz on 2009-05-22
Hi to all,

I'm trying to install the Virtual machine in UBUNTU but I get the following error
message:
  	 	 		 			VirtualBox can't 			operate in VMX root mode. Please disable the KVM kernel extension, 			recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).
 		 	  

  p, li { white-space: pre-wrap; }     Result Code: 
  [FONT= ]NS_ERROR_FAILURE (0x80004005)[/FONT]
   Component: 
  Console
   Interface: 
  IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}







Can anyone help?


Best,
Luis

---

### Post by sdennie on 2009-05-22
Try running:

```

sudo modprobe -r kvm_intel

```

Or, if you have an AMD CPU:

```

sudo modprobe -r kvm_amd

```

If you are then able to run VirtualBox, edit /etc/modprobe.d/blacklist and add the the kvm module to the blacklist to prevent it from being loaded when you boot.

---

### Post by luisridaocruz on 2009-05-25
Thanks for the response.

There are several files under :
/etc/modprobe.d/

[B]alsa-base.conf           blacklist-framebuffer.conf  dkms.conf
blacklist-ath_pci.conf   blacklist-modem.conf        libpisock9.conf
blacklist.conf           blacklist-oss.conf
blacklist-firewire.conf  blacklist-watchdog.conf[/B]

Which one should I edit?
Should I add the following line to such file?

**blacklist kvm**

Best,
Luis

---

