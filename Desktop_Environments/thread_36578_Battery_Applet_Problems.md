---
title: "Battery Applet Problems"
date: 2005-05-23
forum: Desktop Environments
---

### Post by mis@nthrope on 2005-05-23
Hello, I'm a new Linux user using Ubuntu (migrating from Windows) on my laptop. I'm having trouble with the battery applet that lives in the upper right panel. It says that the battery is almost dead when in fact it's at full power and my laptop is plugged in. Other times it just crashes. Is there any way to fix this? Thanks for any help.

---

### Post by ghostrifle on 2005-05-24
Are you sure that you are running the right kernel for your system ?

For example: I'm having an Athlon Mobile and I'm running linux 2.6.10-5-k7 now. Before running this kernel version I had the same problems. But now everything is fine. :-P 

Maybe this helps and if not, post your system configuration

---

### Post by mis@nthrope on 2005-05-25
I don't know which version of the linux kernel I'm running. I installed Ubuntu from the Intel x86 install CD iso image burned onto a CD. How do I check which version of the kernel I'm running? My system configuration is Dell Inspiron 2650 with Intel Pentium 4 Mobile.

---

### Post by pampa on 2005-05-25
It is almost for sure that you are using the i386 kernel.  If that is a centrino laptop you need the i686 kernel.  It is not that the i386 will not work with your computer, but the other is optimized for your processor.

In order to install the i686 kernel go to System > Administration > Synaptic Package Manager.  In the application, go to seach and put "linux-686".  Double-click on that package and accept all the other packages that are needed.  After it download and install de package, reboot.  Now you should be using the new kernel.

Even if I gave you all the explanation of how to install the version of the kernel, I don't know if that is going to solve your problem with the battery applet.

---

