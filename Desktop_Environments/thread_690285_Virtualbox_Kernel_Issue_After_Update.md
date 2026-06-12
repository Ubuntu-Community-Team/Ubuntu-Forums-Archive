---
title: "Virtualbox Kernel Issue After Update"
date: 2008-02-07
forum: Desktop Environments
---

### Post by ronswift on 2008-02-07
I am running Ubuntu Dapper. I installed Virtualbox a month ago and configured it to run Win2k workstation. It ran just fine. After a recent update, I am getting this error when I attempt to run the Win2k workstation in Virtualbox:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 When I try to modprobe vboxdrv I get FATAL: Module vboxdrv not found.
The device no longer exist in /dev/vboxdrv
I am using kernel 2.6.15-51-386
I think that one of my updates added a new kernel that either doesn't support Virtualbox or I need to reconfigure Virtualbox for this kernel. I have Virtualbox running on another workstation with Ubuntu Gutsy and I am not encountering these issues. The dapper workstation is my main system at the office and I do not want to upgrade it until the next long term release, Hardy. 

Help

---

### Post by ronswift on 2008-02-07
Issue solved. I had to install the linux headers for the new kernel then re-install Virtualbox and everything worked.
The kernel version can be found using the command uname -r.
Then use sudo aptitude or apt-get install linux-headers-'uname -r'
I hope that helps anyone else who may have experienced this problem.

---

