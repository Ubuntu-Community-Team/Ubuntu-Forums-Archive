---
title: "How to permanently remove Wifi module?"
date: 2005-11-26
forum: Desktop Environments
---

### Post by Neobuntu on 2005-11-26
After the auto update of the 2.6.12-10-k7 image, the acx_pci modules conflict with the NDISwrapper driver.

A simple sudo rmmod acx_pci makes the Wifi smooth and 100% with the wrapper driver only.

Why does the new Kernel handle this differently?

I forgot or never knew how to make this permenent. Would you please help find the easiest method?

Thank you for you help.

---

### Post by kairu0 on 2005-11-26
Is acx_pci listed in your /etc/modules file?

---

### Post by Neobuntu on 2005-11-26
It is not in my /etc/modules file. That's why I'm wondering what's going on. 

It must be a module if rmmod removes it but where is it being loaded?

How do I stop it from loading at boot.

Is it a "hotplug" issue?

Edit:

Yep, I put it "acx_pci" in the hotplug blacklist and all is well.

---

