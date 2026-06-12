---
title: "Nvidia drivers in latest kernel"
date: 2009-05-13
forum: General Help
---

### Post by momist on 2009-05-13
Hi there,

I'm still running Intrepid on a 32 bit machine with an Nvidia FX5200 graphics card.  Since the updated kernel was installed two days ago, I have been restricted to low resolution graphics. Yeuch.

I've tried several ways to fix this without success.  Synaptic has loaded the 173 drivers, but when I try to change Nvidia X server settings from the Administration - NVIDIA menu I get this message:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I've run the command as root and restarted the X server using Alt Ctl Backspace, but the system complains it can't find the drivers.  Can anyone suggest a cure please?

Ta very much.

---

### Post by Zimmer on 2009-05-13
Do you have the headers installed for the latest kernel??
When you have (and if that does not resolve the issue )it might be an idea to uninstall the nvidia drivers  and reinstall them so that the module is freshly loaded into the new kernel.

(kernel updates have had a habit of lacking the Nvidia modules... )

---

### Post by momist on 2009-05-13
Thanks for the response Zimmer, but I don't know how to find if the "headers" are installed.  I believe I have uninstalled and reinstalled the drivers already, in my various messing around, but still no joy.

Previous updates have had a similar effect, and then the "add/remove" facility has cured it, but not this time.

---

### Post by momist on 2009-05-13
More information on my problem:

I have tried removing the Nvidia drivers through "Add/Remove", followed by "Completely remove" everything Nvidia related in Synaptic Package Manager, and then re-installed the NVidia binary X.Org driver ('version 173' driver) using "Add/Remove".  On reboot I get the following message:

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

I next get a message letting me boot into low resolution graphics.  This offers other options regarding adjusting the configuration, but I don't have the knowledge to pursue that.

Sysinfo tells me that I have 
Kernel : 2.6.28-11-generic
Xorg version: unknown (09 March 2009  10:48:54AM)

Can anyone tell me how to fix this please?

Ta very much!

---

### Post by Zimmer on 2009-05-14
look in synaptic 
linux-headers-2.6.28-11 ....

ensure you have the corresponding headers for your linux-image

the linux-ubuntu-modules
and, maybe,
linux-restricted-modules (not sure at this point if they are required.)
I use envyNG on Hardy and have just applied an updated kernel without any ill effect, in fact I watched the detailed messages announce it had loaded the Nvidia module..)
I will go and look at some earlier posts on this....

---

### Post by momist on 2009-05-14
> **Zimmer said:**
> look in synaptic 
linux-headers-2.6.28-11 ....

ensure you have the corresponding headers for your linux-image

<snip>
I will go and look at some earlier posts on this....

Thanks for the pointer Zimmer.  I've had a look in synaptic, and there are no headers there for this kernel.  That may explain my problem!

Well, I've edited my /boot/grub/menu.lst to use the older kernel 2.6.27-14-generic, and after flushing out everything nvidia* I've used Add/Remove to reinstall the Nvidia drivers for that kernel; and now all is well.

I find it rather annoying that a system that is supposed to "just work" will suggest an upgrade to a newer kernel that does not offer support for my graphics card.  Uh-Well, as my son used to say.  I have been living an interesting life. 

Thanks for your help with this, and I hope the thread informs some other users with this problem.

---

