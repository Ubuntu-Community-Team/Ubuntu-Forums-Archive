---
title: "Ati to GeForce"
date: 2005-10-31
forum: Desktop Environments
---

### Post by Janna on 2005-10-31
Hi,

I had Ubuntu running with onboard ATI radeon Express driver but then I bought a geforce 6600 card.

I ran apt-get install nvidia-glx
and then sudo nvidia-glx-config enable
That gave me some error message about not being able to change and told me to go into xorg.conf manually to change nv to nvidia.

I opened xorg.conf but all it had was the stuff from ATI.

Can somebody please advise me how to uninstall ATI drivers from command line and install geforce 6600?

Thanks

---

### Post by RAOF on 2005-10-31
Run "sudo dpkg-reconfigure xserver-xorg".  This will allow you to re-set-up your xorg.conf.  Select the "nvidia" driver when asked (it will probably default to the "nv" driver.  This is also ok, but won't get you 3d acceleration).

Additionally, it might be a good idea to disable your onboard video too, if you can.  It might confuse things :)

---

