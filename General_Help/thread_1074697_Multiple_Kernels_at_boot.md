---
title: "Multiple Kernels at boot"
date: 2009-02-19
forum: General Help
---

### Post by cyclonedr on 2009-02-19
Hi all,
  At the GRUB menu I have an option to select three different kernel versions, I think the extensions range from .14 to .16, which installed recently.  Right now I don't have any problem with three different kernels, but after a while there will most likely be more than three.  For future reference I'm wondering either how to remove the old kernel, or remove the entry.  Thanks for any suggestions or tips. 
Cyclone

---

### Post by drs305 on 2009-02-19
The link in my signature line for StartUp-Manager is to a tutorial which was originally written to discuss multiple kernel displays in menu.lst

It discusses how to install and use SUM as well as manual editing tips. 

You can also limit the number of kernels displayed by uninstalling older kernels via synaptic. Once they are removed they will not be displayed on boot. How to do this is also presented.

SUM has a lot of useful menu.lst tweaks that allow you to change grub's settings without manually editing menu.lst

---

### Post by cyclonedr on 2009-02-19
Thanks, that helped a lot

---

