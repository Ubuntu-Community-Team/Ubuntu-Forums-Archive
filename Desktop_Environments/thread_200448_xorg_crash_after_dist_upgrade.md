---
title: "xorg crash after dist upgrade"
date: 2006-06-20
forum: Desktop Environments
---

### Post by pratzabrat on 2006-06-20
The notification bar on my desktop indicated that there were updates awaiting dl, so I did this
> sudo apt-get dist-upgrade
A new Linux image I am told was installed. It required a restart, so I did that. After than my xorg just dint start. So I reverted back to an old xorg.conf file I had in backup. I realised that my Nvidia GC was no more recognized. So I went about the normal way of installing the graphics card. 

> sudo apt-get install nvidia-glx nvidia-kernel-common

But my graphics was not installed!!! Wud do w/ some guidance. Thanx

---

### Post by tseliot on 2006-06-20
Try this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED")

Next time, please use the Search function of the forum. Lots of users had the same problem before.

---

