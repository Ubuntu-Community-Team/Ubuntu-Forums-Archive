---
title: "Launcher (and other stuff) act weird after update."
date: 2012-08-27
forum: Desktop Environments
---

### Post by Poodl3 on 2012-08-27
After about 6 months of win7 i decided to try out ubuntu again.

Updated to 12.04 today, but now starting ubuntu is a real pain.

First, it looks like a second desktop is launched on top of the first one. 

Secondly, the launcher-bar is invisible, although it's there because i see the names of the applications when i mouse over them.

Thirdly, applications can be started (from the (invisible) launcher and the terminal), though they can not be seen. But they are there, since both the pointer and the top bar text changes when i start them.
[IMG]http://imgur.com/Bp0Z7[/IMG]
[http://imgur.com/Bp0Z7](http://imgur.com/Bp0Z7)

---

### Post by vexorian on 2012-08-27
this happened to me when I used a kernel version that didn't have the nvidia driver module attached. Probably something about the update you did failed to attach the GPU driver to the new kernel. 

If you use nvidia, try reinstalling the nvidia-current package. For example, you can uninstall it. Reboot and then install it again.

For ATI there is probably a similar workaround.

---

### Post by Poodl3 on 2012-08-27
Hmm, updated the drivers, but this doesn't seem to do any difference at all.

---

