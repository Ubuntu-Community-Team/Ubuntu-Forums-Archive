---
title: "Latest 14.04 kernel update messed up graphics/system"
date: 2015-01-13
forum: Desktop Environments
---

### Post by iansan on 2015-01-13
I'm using Ubuntu 14.04 64-bit on a new SSD drive and after updating to the latest kernel release yesterday I can no longer use the system outside of the shell. The system boots up and I'm presented with the login dialog, but at a much lower resolution than before. Once I log in I cannot see any items on my Desktop, I cannot see the launcher even after pressing the Windows key on my keyboard, and right-clicking on the Desktop does nothing.

My graphics card is a MSI geforce gtx 970 and I'm using the Nvidia CUDA drivers. I tried booting into older kernels but they don't work at all (blank screen on boot), as well as [deleting the problematic kernel]("http://www.upubuntu.com/2012/09/how-to-repair-broken-system-after.html") but I'm still getting the same behavior. I want to avoid reinstalling if I can avoid it, and reinstalling and updating to this kernel again could very well do this all over again.

Is there something else that I can do here?

---

### Post by ajgreeny on 2015-01-13
Did you try reinstalling the graphics driver for the new kernel?

---

### Post by iansan on 2015-01-14
Yes I reinstalled the Nvidia.deb from the command line with dpkg, rebooted, and logged in but still have the same problem.

---

### Post by iansan on 2015-01-20
I finally got this fixed, will share my solution in case anyone else runs into this:

1. Drop into the command line with ctrl-alt-F1
2. Stop X with sudo service lightdm stop
3. cd to the directory where the Nvidia driver installation script is
4. sudo su root
5. sh Nvidia_install_script.run --update
6. Follow prompts to install latest version of driver
7. sudo service lightdm start

---

