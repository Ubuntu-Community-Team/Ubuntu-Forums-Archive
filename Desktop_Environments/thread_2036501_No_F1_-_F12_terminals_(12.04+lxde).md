---
title: "No F1 - F12 terminals (12.04+lxde)"
date: 2012-08-02
forum: Desktop Environments
---

### Post by scu-ba-de-buntu on 2012-08-02
I am using Ubuntu 12.04LTS + lxde meta deb pack, so I am not sure if the cause is LXDE, but when I press one of the function keys to drop down to terminal to resolve a faulty program or crash, all that I get is a red-ish bar at the top of the screen. Pressing F7 i believe brings me back to X11, but this is a serious problem because it prevents me from fixing problems. Any ideas?

Edit: I meant Ctrl+Alt+functionKey, not just the functionkey by itself

---

### Post by markbl on 2012-08-02
You mean you don't get a virtual terminal when you press ctrl+alt+f1?

If that is what you mean, and you have an nvidia graphics card, then you possibly have [this bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1016457)?

---

### Post by Bobhuber on 2012-08-02
Try adding vga=normal to your /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset vga=normal"
This is used with the Nvidia problem in 12.04

---

### Post by scu-ba-de-buntu on 2012-08-02
> **markbl said:**
> You mean you don't get a virtual terminal when you press ctrl+alt+f1?
Yeah, my bad, I meant ctrl+alt+Functionkey

> **markbl said:**
> 
If that is what you mean, and you have an nvidia graphics card, then you possibly have [this bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1016457)?
It is an nvidia card, or at least NVidia-based. The exact card is a EVGA GeForce GTX 670 FTW. I would have mentioned the card, but I didn't think it would be a graphics bug since everything else seems to work fine. I am reading through the Bug report now.

> **Bobhuber said:**
> Try adding vga=normal to your /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset vga=normal"
This is used with the Nvidia problem in 12.04
I will try this as soon as I get back to the machine. I'll add an edit or something for an update.


-----------------------------

EDIT #1: Note, this was not an issue when using a HDD loaded with 10.04LTS running all the same hardware.

---

### Post by markbl on 2012-08-02
> **scu-ba-de-buntu said:**
> I am reading through the Bug report now.
Note there is little activity on that bug but if you look around the linux forums you will find this is a common problem in all recent versions of the nvidia driver (i.e. v295.*, v302.*, v304.*). It is not a problem specific to ubuntu. The problem goes away if you swap to nouveau driver. Also, virtual terminals had worked fine for me for years previously using exact same hardware on nvidia.

---

