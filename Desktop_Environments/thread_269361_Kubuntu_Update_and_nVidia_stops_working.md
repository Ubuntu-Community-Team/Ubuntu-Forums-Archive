---
title: "Kubuntu Update and nVidia stops working"
date: 2006-10-01
forum: Desktop Environments
---

### Post by rianquinn on 2006-10-01
I just installed Kubuntu, and did an update (first thing). The update includes kernel 2.6.15.27.

Then I

1) apt-get install nvidia-glx
2) changed "vesa" to "nvidia" in my xorg.conf file.

When I reboot XServer hangs. However, if I boot into kernel 2.6.15.25 XServer boots properly.

If I boot via "Command Prompt" and run startx, I get an error about the nvidia module not being able to load when using 2.6.15.27.

What should I do. I need to be able to boot into 2.6.15.27 because I use Qemu and it won't compile with using the Latest Kernel.

---

### Post by Jucato on 2006-10-01
Make sure that linux-restricted-modules-2.6.15-27 is installed.

Whenever you update/install a new kernel, make sure that the linux-restricted-modules that matches the version of the kernel is also installed. You might have to enable dapper-security restricted repositories to do that.

Also, when you install nvidia-glx, you don't have to manually change "vesa" to "nvidia". You use a command like

[code]sudo nvidia-xconfig[/config]

---

### Post by rianquinn on 2006-10-01
Thanks for the help. I looked at the linux-restricted-modules and xxx-27 wasn't there. Googled the problem and it was because I needed to add 

restricted

to dapper-security repository. I guess Kubuntu didn't do this for me. After I added this and did an apt-get update, apt-get upgrade and the modules downloaded themselves and the problem was gone. 

Thanks

---

