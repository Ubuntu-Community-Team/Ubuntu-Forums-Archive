---
title: "Passing Options to Kernel Modules At Startup"
date: 2006-01-14
forum: General Help
---

### Post by mlalkaka on 2006-01-14
I've been using Linux for about two years now, but when it comes to kernel modules and modprobe, I'm still a rookie.

I have a webcam that uses the spca5xx kernel module. The module is working properly with my camera. But in order to get the correct colours, I have to load the module with the option "force_rgb=1". However, when my computer starts up, the module loads without this option. How can I pass this parameter to the module when it loads during startup?

Thanks.

---

### Post by stuporglue on 2006-01-14
I believe you just need to edit /etc/modules and add a line with the module name and parameters:

spca5xx force_rgb=1

then reboot and try it. :-)

---

### Post by dcstar on 2006-01-14
[QUOTE=mlalkaka]I've been using Linux for about two years now, but when it comes to kernel modules and modprobe, I'm still a rookie.

I have a webcam that uses the spca5xx kernel module. The module is working properly with my camera. But in order to get the correct colours, I have to load the module with the option "force_rgb=1". However, when my computer starts up, the module loads without this option. How can I pass this parameter to the module when it loads during startup?

Thanks.[/QUOTE]
Have a read of the modprobe man page, and a look in your /etc/modprobe.d directory for examples.

---

### Post by mlalkaka on 2006-01-14
Thanks for the replies. I tried your way, dcstar, and it worked. I had read the modprobe man page earlier, but I could never find the modprobe.conf file of which it described. Then I realized that the files in /etc/modprobe.d/ have the same format as that described in the man page of modprobe.conf. I made a new file in /etc/modprobe.d and used the 'options' command; it worked.

---

