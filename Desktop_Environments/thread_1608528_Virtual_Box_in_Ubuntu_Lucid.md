---
title: "Virtual Box in Ubuntu Lucid"
date: 2010-10-29
forum: Desktop Environments
---

### Post by chinna saaeb on 2010-10-29
I have a problem in using virtual box. The output on the console is as follows

VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/opt/VirtualBox/VirtualBox.so",) failed: VBoxVMM.so: cannot open shared object file: No such file or directory

Till recently it was working well.
I am using Ubuntu Lucid and it is updated online periodically. The current kernel version is Linux 2.6.32-25-generic 
After upgradation I re run the Virtual Box setup. (/etc/init.d/vboxdrv setup so I rule out this due to kernel upgradation)
The Virtual Box version is i386 and the package is  VirtualBox-3.2.4-62467-Linux_x86.run 
Kindly advise

---

### Post by celldweller1591 on 2010-10-29
To fix, su to root and issue the following commands:
> cd /opt
ln -s libdirectfb-1.2.so.0 libdirectfb-1.0.so.0
ln -s libfusion-1.2.so.0.8.0 libfusion-1.0.so.0
ln -s libdirect.so libdirect-1.0.so.0

Also check for any other links : ldd /usr/lib/virtualbox/VirtualBox.so
These commands will create symbolic links for the missing libraries. Hope this helps.

---

### Post by techmix on 2010-11-01
Well, linking missing libraries didn't worked for me. (I think I had missed some libraries or something..) 
Instead, this solved the problem:

Change the Run-Path of all shared libraries in /opt/VirtualBox to "/opt/VirtualBox"
* in my case, the previous r-path was "$ORIGIN". So I had to change it to some path that is 7 characters or less. I made a symbolik link to /opt/VirtualBox (say /opt/vb) and replaced "$ORIGIN" with it:
```
sudo chrpath *.so -r /opt/vb
```

---

