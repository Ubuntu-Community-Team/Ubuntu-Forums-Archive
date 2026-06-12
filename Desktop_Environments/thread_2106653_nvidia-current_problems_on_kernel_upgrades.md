---
title: "nvidia-current problems on kernel upgrades"
date: 2013-01-19
forum: Desktop Environments
---

### Post by rotten777 on 2013-01-19
So I've realized I'll NEVER have a perfectly functional nvidia binary driver and Ubuntu setup. So I've made a workaround.

Evidently, the nvidia-current package is responsible for building the kernel module and doesn't fail when there are no headers for the current kernel and therefore the module doesn't get built and lightdm looks like poop and doesn't work.

```
#!/bin/bash
apt-get -y remove nvidia-current 
apt-get -y install build-essential linux-source linux-headers-`uname -r`
apt-get -y install nvidia-current
modprobe nvidia_current
lsmod | grep nvidia
/etc/init.d/lightdm restart

```

There's my fix. Save that to ~/nvidia-fix.sh then chmod +x ~/nvidia-fix.sh
You have to run with sudo as all the commands require superuser access.
I hope this helps others.
:popcorn:


Explanation of the code...
The first line removes the nvidia package, the second line pulls the headers for your current kernel, third reinstalls the nvidia package which can now build the kernel module, fourth line loads the kernel module, fifth line checks to see if the module is loaded and outputs to the terminal, sixth line restarts the lightdm service which should move to the logon screen.

This works on 12.10-AMD64. Should be universal though.

---

