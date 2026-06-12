---
title: "Kernel update destroyed my screen resolution"
date: 2009-01-10
forum: General Help
---

### Post by Robotman on 2009-01-10
Hi, After updating my Xubuntu 8.04 to kernel 2.6.24-23, I can only get a screen resolution of 640x480.  I was previously using 1600x1200, but I can't seem to get that resolution back.
Can someone help me out on this?

---

### Post by ajgreeny on 2009-01-10
If you are running an nvidia or ati restricted driver, you will probably need to install it again for the new kernel.

---

### Post by Robotman on 2009-01-10
I use Nvidia restricted drivers.  I used Synaptic Package Manager to "reinstall" the Nvidia packages that were already installed (nvidia-glx-new and nvidia-kernel-common).  After that, I went to "Hardware Drivers" and enabled the Nvidia driver.  I logged out and back in and now my screen resolution is worse than it was before and the only options I have to change them are "Default" and 320x240.

---

### Post by Robotman on 2009-01-10
I think I've fixed everything.... I went back and uninstalled the Nvidia driver through the "Hardware Drivers" screen (by un-checking it) then shut down the computer.  I then booted up again, then shut down again.  Then I booted up and reinstalled the Nvidia driver (through Hardware Drivers) and shut down.  I just booted and now I have my old 1600x1200 screen resolution back.
Thanks for the help ajgreeny, I just had to try it a couple of times. ;)

---

