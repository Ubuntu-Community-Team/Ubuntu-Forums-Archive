---
title: "Windows XP Pro in Virtual Box OSE"
date: 2009-09-26
forum: Desktop Environments
---

### Post by xtiano77 on 2009-09-26
I am trying to install Windows XP Pro in a virtual box using Virtual Box OSE. I am giving it 524 MB of local hard drive as the drive for the virtual box. I have also tried using a virtual drive, but on both instances I am getting the following message:


VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


Can anyone help me out with this? I don't want to mess up anything that would cause me to reinstall the entire OS.  Thanks in advance for your help.

---

### Post by gordintoronto on 2009-09-26
When you read the system requirements on the XP Pro box, what does it say about hard drive space?  I suspect it requires 5 GB or so...

---

### Post by urugTON on 2009-09-27
The error has to do with the fact that you have VMX capabilities in your CPU, BIOS and Kernel.  VirtualBox is not happy with that combination.  You'll have to find a way to make VBox happy.  You'll likely have to unload the KVM modules in your kernel.

I ran into this as well, but I just moved Virtual Box to an older machine.  I've very happy with VBox, BTW. 

I'm running KVM on the machine where VBox complained.

BTW, you'll have to find more than 524 Mega Bytes of disk.  My very skinny real live XP system takes 6 Gigabytes out of a 12 GB partition.

---

### Post by teitzelb09 on 2009-09-27
i have a problem too. installing the windows xp on the VM. i have the disc in. but it just says


FATAL: No bootable medium found! System halted.



btw im new..


EDIT:   Fixed. i just mounted it. now i feel retarded

---

### Post by gordintoronto on 2009-09-28
> **urugTON said:**
> The error has to do with the fact that you have VMX capabilities in your CPU, BIOS and Kernel.  VirtualBox is not happy with that combination.  You'll have to find a way to make VBox happy.  You'll likely have to unload the KVM modules in your kernel.

I ran into this as well, but I just moved Virtual Box to an older machine.  I've very happy with VBox, BTW. 

I'm running KVM on the machine where VBox complained.

Is there some way to display the presence or absence of VMX capabilities?  I'm running a current kernel with Jaunty, on an AMD Phenom II X2 CPU, and VirtualBox runs very nicely.

---

### Post by xtiano77 on 2009-09-28
I am giving it 100GB of hard disk space. The 524 was the amount of ram I am allowing it to use.

---

### Post by urugTON on 2009-10-02
To check that you machine has the virtualization hardware available do the following:

```
egrep '(vmx|svm)' --color=always /proc/cpuinfo
```

If you get any output, the feature is active.  FWIW, vms is Intel, svm refers to AMD.

More info here: [http://100days.de/serendipity/archives/95-Virtualbox-and-VMWare-not-running-on-Ubuntu-9.04-due-to-KVM-kernel-module.html](http://100days.de/serendipity/archives/95-Virtualbox-and-VMWare-not-running-on-Ubuntu-9.04-due-to-KVM-kernel-module.html)

---

