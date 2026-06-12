---
title: "Stuck updating / missing kernel"
date: 2009-05-14
forum: General Help
---

### Post by tjotser on 2009-05-14
I've recently compiled a new kernel, and removed it after, but now when i try to get updates, it makes me run in circles.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Then i do "sudo dpkg --configure -a"


"Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.30-rc5-candela
Cannot find /lib/modules/2.6.30-rc5-candela
update-initramfs: failed for /boot/initrd.img-2.6.30-rc5-candela
dpkg: subprocess post-installation script returned error exit status 1"

what can i do, as nothing will update ? 
Thanks for your help.:KS

---

### Post by npallett on 2009-05-15
I have exactly the same problem.

I built my own kernel to try to fix the bluetooth dongle problem reported in other threads, but my bluetooth dongle still doesn't work, so I uninstalled the new kernel, and went back to using stock kernels.

Now when I try to run udates, I get the following:

When I run "apt-get upgrade" I get:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

When I run "sudo dpkg --configure -a", I get:

----------------------------------------------------------------

Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28.9
Cannot find /lib/modules/2.6.28.9
update-initramfs: failed for /boot/initrd.img-2.6.28.9
dpkg: subprocess post-installation script returned error exit status 1

----------------------------------------------------------------------

So now, I cannot update my system.

---

### Post by tjotser on 2009-05-15
Great ! you have the same problem as me ! :P Now all we need is someone that will be able to tell us if we should re-install or not.. ..
I dearly hope not ..will check back in 8 hours

---

### Post by npallett on 2009-05-17
Try the following command:

update-initramfs -d -k 2.6.30-rc5-candela

---

