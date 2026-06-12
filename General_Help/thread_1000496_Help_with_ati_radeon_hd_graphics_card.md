---
title: "Help with ati radeon hd graphics card"
date: 2008-12-03
forum: General Help
---

### Post by munit5000 on 2008-12-03
Hey I just installed ubuntu on my new laptop today transitioning from windows. Right now everything is great except I don't have any drivers for my graphics card, which is the ATI Radeon HD 3560. I went to the amd website to get the new driver and downloaded the one for radeon hd 3xxx series, ran it, but still am not being able to use desktop effects.

I don't know how to run amdccle either and when I was prompted to download a driver by ubuntu, fglrx, when enabling desktop effects the window crashed. Everything is new to me! 

Could anyone offer me some help please?

---

### Post by Tilex on 2008-12-03
Hi, 

Please first update your system to have the latest drivers:

```

sudo apt-get update
sudp apt-get dist-upgrade

```

Then, go to System->Hardware driver manager

You will be able to activate the proprietary ATI driver.  If you activated the driver properly, an icon will appear in the taskbar asking to reboot.  

Reboot, and it should be fine.

---

### Post by munit5000 on 2008-12-03
I updated, rebooted, then activated the driver. But no prompt showed up in the taskbar. Now fglrxinfo doesn't work, and desktop effects still cannot be enabled.

Also, when I updated, it installed the latest kernel. How can I delete older kernel versions so they don't show up in the boot menu? (I think it's called grub)

---

### Post by munit5000 on 2008-12-03
I restarted the computer and your solution worked, appreciate your help. I'll try to be more patient from now on.

Any way to delete old linux kernels from the boot menu?

---

### Post by sambarusty on 2008-12-03
Have you tried System->Administration->Hardware Drivers, should pop up with a proprietary driver you need and ask you if you want to activate it.

---

### Post by jocko on 2008-12-03
> **munit5000 said:**
> Any way to delete old linux kernels from the boot menu?

Just uninstall it from synaptic. The package name is linux-image-2.6.27-[COLOR=Blue]XX[/COLOR]-generic, just make sure you keep at least one kernel.

---

### Post by PocketDog on 2008-12-03
To remove the old kernels ```
gksudo gedit /boot/grub/menu.lst
``` Back up menu.lst first (save as menu.lst.bak). Remove the unwanted kernels there, or comment them out with a #

---

### Post by munit5000 on 2008-12-03
Thanks for the help guys. I don't have any more problems for now so someone should tag this post with [resolved].

---

### Post by Tilex on 2008-12-03
> Thanks for the help guys. I don't have any more problems for now so someone should tag this post with [resolved].

You can do this in Thread Tools -> Mark as resolved

---

