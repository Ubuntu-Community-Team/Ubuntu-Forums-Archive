---
title: "Nvidia 8800GT on Ubuntu 8.04 (possible solution)"
date: 2008-05-28
forum: Desktop Environments
---

### Post by cbkm on 2008-05-28
Hi guys,

I was recently using the NVIDIA installer (from gutsy days) when the kernel upgrade recently encouraged me to get the Ubuntu packages working... 

Here's what I did...

1) sudo ./nvidia-installer --uninstall
2) sudo apt-get install linux-restricted-modules-`uname -r`
3) sudo apt-get install nvidia-glx-new
4) sudo /etc/init.d/gdm restart

However after those steps my Xorg.0.log file was showing a failure to load the driver and a look at dmesg showed that the kernel version being loaded was "96.43.05" and the client was "169.12". Odd since I'd installed nvidia-glx-new.

So I dug a bit further and discovered that lrm-video had the code to load the appropriate kernel module (nvidia_new) but it obviously wasn't being used. Digging slightly further I found the file /etc/modprobe.d/lrm-video which seemed to want to use lrm-video but all the install ... lines were commented out.

After uncommenting all the install... lines I did the following:-

1) sudo /etc/init.d/gdm stop (it was still lingering in low-res mode)
2) sudo pkill X (just to be sure)
3) sudo pkill gdm (just to be sure)
4) sudo rmmod nvidia (old kernel driver still loaded)
5) sudo /etc/init.d/gdm start

...and it all fired up perfectly.

Apologies if this is a duplicate I just basically wanted to post about the commented lines in the modprobe.d lrm-video file which seem to stop the correct driver being loaded.

---

