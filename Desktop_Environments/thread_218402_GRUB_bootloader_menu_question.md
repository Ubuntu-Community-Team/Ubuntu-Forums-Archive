---
title: "GRUB bootloader menu question"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Epperly on 2006-07-18
Hi, on the bootloader menu it looks like this:

Ubuntu, kernal 2.6.15-26-386
Ubuntu, kernal 2.6.15-26-386 (recovery mode)
Ubuntu, kernal 2.6.15-25-386
Ubuntu, kernal 2.6.15-25-386 (recovery mode)
Ubuntu, kernal 2.6.15-23-386
Ubuntu, kernal 2.6.15-23-386 (recovery mode)
Ubuntu, memtest86+
Windows

Now, why does it show all those kernals with slightly different variations? I use the top one of course but should the 25 and 23 ones be there? If not, how would I get rid of them?

It seems every once in a while the list builds up like that, it started with just the 23 and recov, memtest and windows, now it has those other 4...

Thanks

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **Epperly said:**
> Hi, on the bootloader menu it looks like this:

Ubuntu, kernal 2.0.15-26-386
Ubuntu, kernal 2.0.15-26-386 (recovery mode)
Ubuntu, kernal 2.0.15-25-386
Ubuntu, kernal 2.0.15-25-386 (recovery mode)
Ubuntu, kernal 2.0.15-23-386
Ubuntu, kernal 2.0.15-23-386 (recovery mode)
Ubuntu, memtest86+
Windows

Now, why does it show all those kernals with slightly different variations? I use the top one of course but should the 25 and 23 ones be there? If not, how would I get rid of them?

It seems every once in a while the list builds up like that, it started with just the 23 and recov, memtest and windows, now it has those other 4...

Thanks

You can safely remove the 2.6.15-23/25 kernels because they are outdated. Remove them in synaptic by searching for 2.6.15 and then mark them for removal. Once they are removed their entried will be removed from the grub menu.

---

### Post by brownrl on 2006-07-18
I took the extra lines out of my grub just recently leaving only the main one and the recovery. You should probably take out the windows one too. ;) 

i think they get added when the kernel gets upgraded. Good safety measure just in case.

---

### Post by Athropos on 2006-07-18
Each time a new kernel is released, and installed on your machine, Grub is updated to use this new kernel by default. The update manager does not automatically uninstall previous kernels, for safety reasons. When a new kernel has been released, and you sure it's working correctly on your system, you may uninstall the previous version by yourself thanks to Synaptic.

---

### Post by mrbaz on 2006-07-18
By not totally replacing the kernel every time that it gets upgraded allows you to gracefully go back to the previous version before the update if it inadvertently screws something up.

---

### Post by DoorGunner on 2006-07-18
The updater will add more kernels periodically. You just need to go into

$sudo gedit /boot/grub/menu.lst

You can delete all the ones you no longer require. In your case just remove

Ubuntu, kernal 2.0.15-25-386
Ubuntu, kernal 2.0.15-25-386 (recovery mode)
Ubuntu, kernal 2.0.15-23-386
Ubuntu, kernal 2.0.15-23-386 (recovery mode)

kernel 2.0.15.26-386 is the most current

you can also go to 
/boot/ and remove any vmlinuz, initrd, etc that does not have the latest data....

word of advice....it is always nice to keep your last kernel variation incase the new one doesnt work properly.

---

### Post by VirtuAlex on 2006-07-18
I usually keep one back just in case. I was configuring wireless card once and driver got messed up, so even recovery mode was hanging on boot. I had to boot to older kernel to fix the driver. Of course you can use live CD for that, but what the heck if old kernel is already there with all your configurations.

---

### Post by Epperly on 2006-07-18
oops, yeah 2.6 not 2.0 heh... anyway, thanks I guess I'll keep 25 just in case, even though I've had 26 for a while and it hasn't done anything wierd thus far.

Thanks!

Do I mark it for removal or complete removal?

---

### Post by Athropos on 2006-07-19
> **Epperly said:**
> 
Do I mark it for removal or complete removal?

I personally use complete removal.

---

