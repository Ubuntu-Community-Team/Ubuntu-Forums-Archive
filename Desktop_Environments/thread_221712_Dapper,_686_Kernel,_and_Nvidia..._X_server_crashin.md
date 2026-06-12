---
title: "Dapper, 686 Kernel, and Nvidia... X server crashing."
date: 2006-07-23
forum: Desktop Environments
---

### Post by joeq4u2 on 2006-07-23
Ok, my problem is that when I install the nvidia-glx driver and reconfigure the xorg.conf file the x server fails to start.

The worst part is I had it working with no problems on this very system with the same configuration I'm working with now, but I reinstalled the system because I wanted to try out SLED 10.

Anyway this is Dapper running gnome and after installing I download all updates and then install the 686 kernel.  Next I tried installing the nvidia-glx driver which goes fine, but as soon as I reconfigure the xorg.conf file (the same way I've done with the previous working istalllation) it crashes.  If I change it back to "nv" it works fine, but as soon as it uses "nvidia" it crashes.  This is the second time I've installed it trying to get it working.

Anybody have any idea what I need to do?

---

### Post by invalid on 2006-07-23
If you post the error here, we might can guess a little better.

For now, I might suggest that you are missing the restricted modules for your specific kernel. Try installing these, and restarting X.

---

### Post by autocrosser on 2006-07-23
What error messages are you getting? Have you looked at your Xorg.0.log--or better yet--your Xorg.0.log.old  (the replaced log from the 0.log) to see what has caused the prob? Your logs will be in /var/log--I've got a xorg.conf that works for me--do you need one to reference to?

---

