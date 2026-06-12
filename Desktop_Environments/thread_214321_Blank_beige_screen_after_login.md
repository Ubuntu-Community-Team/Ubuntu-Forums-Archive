---
title: "Blank beige screen after login"
date: 2006-07-12
forum: Desktop Environments
---

### Post by warnickij on 2006-07-12
I have loaded and have been running Breezy for several weeks running under VMware without any problems.

Today after reboot and login with the normal GUI screen I get only a dark beige screen. I have tried different failsafe login modes but the only one that works is command line.

I tried to reset with dpkg-reconfigure but the only thing that changed was the resolution of the login page.

I was working on a network/postfix problem when this occured. I am able to run both apache2 and postfix from the command line so that does not appear to be the issue.

I also have kept up-to-date with updates except for the very newest. I have not updated or installed anything new for about a week.

I have rebooted vmware and the XP OS with no change.

Any help would be appreciated.

Joe

---

### Post by warnickij on 2006-07-18
Is there anyway to step through or analyze the boot process to determine what is not working or not being loaded?

In the mean time I'm learning more of the linux commands. :-)

Joe

---

### Post by redwolf963 on 2006-07-18
When a vmware machine is run in the host os,necessarly the memory address spaces normally allotted to host os  have to be changed to an area of mem that can run the device drivers that would normally be allotted to what you happen to be running in virtual machine.Did you try to do an update?
When the virtual os was ported to vmware,the programmer changed the way the kernel accessed allocated memory addresses.I f you do an update to vmware kernel,you may inadvertently overwrite these address spaces back to default,which will conflict with the original os.
   hope that helps

---

