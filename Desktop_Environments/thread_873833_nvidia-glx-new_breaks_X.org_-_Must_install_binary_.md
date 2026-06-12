---
title: "nvidia-glx-new breaks X.org - Must install binary driver from nVidia:s homepage"
date: 2008-07-29
forum: Desktop Environments
---

### Post by zooounds on 2008-07-29
Now I'm beginning to to swear over this.

I have posted about this before but got no good answer.

I have until now used the binary driver from Nvidia:s homepage (NVIDIA-Linux-x86-169.12-pkg1.run) but now when 169.12 is in the respos, I would like to install it the "correct" way.

I uninstalled the driver with "NVIDIA-Linux-x86-169.12-pkg1.run --uninstall"
Everything worked nice.

I install "nvidia-glx-new" instead and restart gdm.

After some flickering gdm says it must start in failsafe mode.

How do I solve this?!

I have not modified the x.org-file so the server should start nicely.

Can I get X.org to log more verbose? All I see now is that it couldn't find any compatible glx blaha?

---

### Post by zooounds on 2008-07-29
I get following:

 API mismatch: the client has the version 169.12, but
 this kernel module has the version 71.86.04.  Please
 make sure that this kernel module and all NVIDIA driver
 components have the same version.

---

### Post by stchman on 2008-07-29
> **zooounds said:**
> Now I'm beginning to to swear over this.

I have posted about this before but got no good answer.

I have until now used the binary driver from Nvidia:s homepage (NVIDIA-Linux-x86-169.12-pkg1.run) but now when 169.12 is in the respos, I would like to install it the "correct" way.

I uninstalled the driver with "NVIDIA-Linux-x86-169.12-pkg1.run --uninstall"
Everything worked nice.

I install "nvidia-glx-new" instead and restart gdm.

After some flickering gdm says it must start in failsafe mode.

How do I solve this?!

I have not modified the x.org-file so the server should start nicely.

Can I get X.org to log more verbose? All I see now is that it couldn't find any compatible glx blaha?

Just enable the restricted driver.  What model of nvidia card do you have?  Only the newer ones need the 169.12 driver.

---

### Post by zooounds on 2008-07-29
> **stchman said:**
> Just enable the restricted driver.  What model of nvidia card do you have?  Only the newer ones need the 169.12 driver.

I have tried that. I still get the same error.

I have a 8800GT that need the latest driver.

---

### Post by zooounds on 2008-07-29
Here is the same problem again:

[http://ubuntuforums.org/showthread.php?t=818804](http://ubuntuforums.org/showthread.php?t=818804)

And here:

[http://www.nvnews.net/vbulletin/showthread.php?t=112719](http://www.nvnews.net/vbulletin/showthread.php?t=112719)

The latest guy had to reinstall Ubuntu to fix it.

There must be a better solution than that...

---

### Post by zooounds on 2008-07-29
Could this be the problem?

f@air:~$ sudo jockey-gtk
WARNING: /sys/module/nvidia_new/drivers does not exist, cannot rebind nvidia_new driver
WARNING: modinfo for module nvidia failed: modinfo: could not open /lib/modules/2.6.24-20-generic/kernel/drivers/video/nvidia.ko: No such file or directory

---

### Post by kidux on 2008-07-29
> **zooounds said:**
> Could this be the problem?

f@air:~$ sudo jockey-gtk
WARNING: /sys/module/nvidia_new/drivers does not exist, cannot rebind nvidia_new driver
WARNING: modinfo for module nvidia failed: modinfo: could not open /lib/modules/2.6.24-20-generic/kernel/drivers/video/nvidia.ko: No such file or directory

If you compile the binary driver yourself from nVidia, it makes a module specific to the kernel. You may be having conflicts between the module and driver loading, so you should see about removing the old module and seeing if that works.

---

### Post by zooounds on 2008-07-29
> **kidux said:**
> If you compile the binary driver yourself from nVidia, it makes a module specific to the kernel. You may be having conflicts between the module and driver loading, so you should see about removing the old module and seeing if that works.

I have removed it completky - same error.

---

