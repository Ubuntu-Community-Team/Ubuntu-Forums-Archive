---
title: "Explanation of the Kernels"
date: 2005-09-10
forum: Desktop Environments
---

### Post by craigmac on 2005-09-10
Hello, even though I've been running Win PCs and networks for a decade, I am a newbie to Linux. Have installed Kubuntu 5.04 onto an Acer Aspire 1406LC laptop and it is great. Really easy and fun too.  :grin: 

My question is (and maybe the answer is obvious) do the different kernel versions make any difference to the operation. I am running 2.6.10-5-386 but it says that my machine is an i686. Am I missing out on bleeding edge performance with the 386 version (this baby is rock solid so far) or is there not much difference?

If I could benefit from changing to the i686 version, would someone please point me in the direction of a  HOWTO to upgrade to the best version for my P4 2.5GHz? I am happy to do my own reading, just not sure if there is any reason to do the upgrade in the first place.

---

### Post by krusbjorn on 2005-09-10
It's quit easy to upgrade to another kernel: install it via synaptic. If you search for "686" it will show up. There is a package called "linux-686" or "kernel-686" (cant remember which), that selects the packages you need.

Your grub configuration will automatically be updated to boot from your new kernel, so next time you reboot, you'll run the 686 one. Don't uninstall your old kernel, cause if the new one doesnt work (which is of course most likely will), you can press ESC during the grub countdown, and boot from your old one.

Will it be faster? Yeah, but i cant say i've noticed any difference myself.

---

### Post by craigmac on 2005-09-10
Thanks for the quick response krusbjorn. I saw a HOWTO on compiling your own kernel within the forum but I wasn't sure if that was what I really needed to do. I am still unsure of what I am doing and since I got this laptop working so well with the installation that I don't want to screw it up for no reason.

I'll give it a go and see what happens.

---

### Post by krusbjorn on 2005-09-10
The first thing i do when (re-)installing Ubuntu is to install the 686 kernel. After all, it's the kernel my machine is supposed to make best use of :) So no need to be scared. And if it screws up, it's easy to revert to the old kernel.
 
Good luck!

---

### Post by craigmac on 2005-09-10
I just did the upgrade as you suggested - it went very smoothly and now I'm running the 686 kernel. Seems to be quite good. I can't say that it is any different but it's early days. Uptime since kernel upgrade is only 4 mins so maybe I should be patient and try a few things  ;-)

---

