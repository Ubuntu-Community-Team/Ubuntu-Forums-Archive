---
title: "Does the system need to be re-installed ?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by leonardoo on 2006-07-18
Hello. Linux systems are knowns for their great stability. Therfore, i've noticed several problemes on my dapper. 
   I've got an nvidia graphic card (128M X4400), that i've installed following the forum, and eventually the wiki.but, when i've dowload the new kernel package : 386-2.26, it doesent let X boot, because of an X problem. it says, screens found but none usable (i've got just one screen). The same problem is noticed with the 686's kernels (all of them that i've tried).
    My second issue, resids in the fact that when i move the defilement bar quickly, the processeur go to 100% use (i've got a pentium IV 1.7 GHZ with 640 ram), and stays at 100% till i stop (even doing it with a console window, contaning even text). (i've got a 386...23 running kernel now). i notice this processeur issues especially with pdfs, the whole systeme goes too slow when i open pdfs. i've got the impression that the processor wich calculates the images, not the graphical card.
  Another problem i've noticed with the X server, is after a lot of hours of use, the mouse goes to the middle of screen, and refuse to respond, untill i reboot the system, i think it's an X problem i guess.
   With my modem (an usb one : speddtouch), pon doesnt work , i cant establish connexion, my fai've got problems also, but what is amzaing, in the earlyy mourning, pon doesnt work, i reboot, and i get the connexion ...
   Finally, i'm wondering if i have to resintall the system, it was so stable, now i've got the impression i'm loosing the computer, can someone help ? thank you in advance.

---

### Post by asplode on 2006-07-18
> **leonardoo said:**
> Hello. Linux systems are knowns for their great stability. Therfore, i've noticed several problemes on my dapper. 
   I've got an nvidia graphic card (128M X4400), that i've installed following the forum, and eventually the wiki.but, when i've dowload the new kernel package : 386-2.26, it doesent let X boot, because of an X problem. it says, screens found but none usable (i've got just one screen). The same problem is noticed with the 686's kernels (all of them that i've tried).


As far as X11 failing when you upgrade your kernel, that depends on which method you went about installing your NVIDIA driver.

If you downloaded the NVIDIA-blahblahblah-8762.run file ([method 2 in tseliots NVIDIA guide]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")) then you will need to re-run the installer to compile a new NVIDIA module for your new kernel.  It should look something like this:
```
cd *directory-of-installer*
sudo ./*NVIDIA-installer-8762*.run
sudo /etc/init.d/gdm restart
```

Otherwise you could just use the standard ones from the repository if that floats your boat.  It will make it easier next time a kernel upgrade comes around.
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

by the way... what is a defilement bar?

---

### Post by leonardoo on 2006-07-18
A sorry, i've meant the scroll bar .
   In fact, i've used the "sudo apt-get install nvidia-glx etc etc" to get the driver. i've upgraded the kernel many times before, (just using the depots updates); this time, it refuses to work. thanks for your help :) Cordially.

---

### Post by asplode on 2006-07-18
You could try whats mentioned in [this post right here]("http://ubuntuforums.org/showpost.php?p=1237396&postcount=5"), about disabling acpi and see if that helps you out any...

> **leonardoo said:**
> A sorry, i've meant the scroll bar .
   In fact, i've used the "sudo apt-get install nvidia-glx etc etc" to get the driver. i've upgraded the kernel many times before, (just using the depots updates); this time, it refuses to work. thanks for your help :) Cordially.

---

