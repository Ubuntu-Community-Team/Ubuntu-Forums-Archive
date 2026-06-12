---
title: "Virtual box unable to start because of 'VMX root mode'"
date: 2009-03-14
forum: General Help
---

### Post by Admiral Yi on 2009-03-14
Hello,
I'm trying to run virtual box OSE on my Ubutnu 8.10 desktop. I would like to try out some other Linux operating systems in it, with a view to installing Windows Xp for gaming at some point in the future. I downloaded it via synaptic and started it up. I set a virtual machine and created a virtual hard drive to run Open Solaris as a sort of test. However, when I start it up I get this message:  

```

VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot.
VBox status code: -4011 (VERR_VMX_IN_VMX_ROOT_MODE).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}
```

I'm reasonably proficient with Linux, but I don't really understand much of this. I've never done any messing around with the kernel. I tried running it as root, but to no avail. Anyone got a solution? Presumably I have to 'disable the KVM kernel' but I have no idea how to do this, so can someone please show me how?

---

### Post by Admiral Yi on 2009-03-20
Anyone able to help with this?

---

### Post by Admiral Yi on 2009-03-20
Bump

---

### Post by acidviews on 2009-11-01
I have v box running atm in ubuntu 9.10
go to 
system > admin > bootup manager 
be very carefull where u click as you do not want to turn off things you need 
scroll down an find "Full Virtualization i386 and amd64"

Uncheck this box an choose to apply the setting now and not after reboot


good luck

---

