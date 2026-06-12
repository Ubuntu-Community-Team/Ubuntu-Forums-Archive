---
title: "Ubuntu freezes before the desktop even appears"
date: 2022-02-07
forum: Desktop Environments
---

### Post by michaelrago on 2022-02-07
I’m running Ubuntu 18.04. The other day, a box popped up and said “There are updates available” so I allowed it to update. It took about an hour, and I was not expecting it. 

After that, when I restarted my computer, the mouse cursor appeared on a blank screen, but I could not move it. A minute later, the rest of the desktop appeared, and a box that said “The login keyring did not get unlocked when you logged in to your computer” and there’s a space for me to type in my password, but the whole screen is frozen. I cannot interact with it in any way. Eventually the screen goes dark, presumably waiting for some kind of input. 

I am using an HP Envy, and I have Windows on this disk too. I can still boot to windows, and I can boot to Ubuntu with an external drive. I just can’t use my Ubuntu desktop because it gets frozen every time.

Is there a way I can repair whatever files are broken and go back to the way it was without losing all the files on the partition? Or even just back up all the files to an external drive and reinstall Ubuntu, that would be okay too. 

Thanks.

---

### Post by grahammechanical on 2022-02-07
At the Grub boot menu select Advanced Options for Ubuntu and boot from an older Linux kernel and see if that is better. If you choose a Linux kernel with recovery mode it will load to a recovery menu. You get these options

resume - resume normal boot. [This will load to a login screen & desktop using an open source video driver]
clean - try to make free space
dpkg - repair broken packages [enable networking first]
fsck - check all the file systems
grub - update grub bootloader
network - enable networking [necessary if there is a need to download packages from the internet]
root - drop to a root shell prompt
system-summary - system summary

Regards

---

