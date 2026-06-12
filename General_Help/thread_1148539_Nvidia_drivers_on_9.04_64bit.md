---
title: "Nvidia drivers on 9.04 64bit"
date: 2009-05-04
forum: General Help
---

### Post by EstebanM on 2009-05-04
Hi, i need  help installing nVidia drivers on Ubuntu 9.04 64bit in my Dell XPS M1530(nvidia Geforce 8600M GT). 
I have upgrade to 9.04 from 8.10 and try to install the drivers using the following methods: 
 
1)First i tried to install using System->Admin->Hardware Drivers and the loading bar dont go beyond 0%, 
 
2)Then i try installing the drivers provided in nvidia.com but it will not install(it says "Unable to find the kernel source tree for the currently running kernel", but i have installed the build-essential, headers and linux-restricted-modules). 
 
3)At last a try again installing using the first method and now it will load to 100% but the drivers stay unable. When i restart the so it says that the kernel modules cant be found and i select use default config. 
 
I've repeat this methods many times whith no result.Under System->Admin is "Nvidia X Server Settings" so i tink this could causes conflic. 
 
TThank you.

---

### Post by RedSingularity on 2009-05-04
The load bar doesnt move at all for a while.  If you leave it alone for a few minutes (depending on your internet speed) it should install just fine.  It jumps to 100% after a couple minutes.

---

### Post by EstebanM on 2009-05-04
Ok, but now it goes to 100% directly. How i uninstall all the componets of the drivers?

I have this in synaptic(attached image) and Nvidia X Server settings.

---

### Post by oldos2er on 2009-05-04
"Then i try installing the drivers provided in nvidia.com but it will not install(it says "Unable to find the kernel source tree for the currently running kernel", but i have installed the build-essential, headers and linux-restricted-modules). "

 You need to have the source repositories (deb-src) enabled.

---

### Post by EstebanM on 2009-05-04
> **oldos2er said:**
> "Then i try installing the drivers provided in nvidia.com but it will not install(it says "Unable to find the kernel source tree for the currently running kernel", but i have installed the build-essential, headers and linux-restricted-modules). "

 You need to have the source repositories (deb-src) enabled.

How i enable the source repositories? I have to clean the previous failed installations and how i do that?(I put what i have on my system by nvidia X Server setting and in synaptic)

---

### Post by motoaxe on 2009-05-04
you could also just download the install script from Nvidia's site and run it.


(sudo sh ./NVIDIA_....)

The script is smart enough to know your current driver isn't working properly, and it will compile a kernel module and update the required files...

---

### Post by oldos2er on 2009-05-04
> **EstebanM said:**
> How i enable the source repositories? I have to clean the previous failed installations and how i do that?(I put what i have on my system by nvidia X Server setting and in synaptic)

 In Gnome, System, Administration, Software Sources, make sure the box in front of Source Code is checked.

---

### Post by EstebanM on 2009-05-06
> **oldos2er said:**
> In Gnome, System, Administration, Software Sources, make sure the box in front of Source Code is checked.

Still the same problem.

Someone can tell me how to erase all the nvidia drivers that where installed wrong.(in a early reply i put a capture of synaptic, i need to know what packages i have to uninstall)

---

### Post by AbdulRahiem on 2009-05-07
I have had the same problem at each upgrade since gutsy. The following solution has worked for me each time:

Do not boot normally, but take the second boot option "recovery mode".
Then go for the command line option. Do NOT try the 'fix x-server' option.
Go to /etc/X11 and copy xorg.conf to something else, e.g. 'cp xorg.conf xorg.conf.9506' (This assumes that it still contains the original good configuration).
Then, from the command prompt you can run the nVidia script. When it comes to the line "Unable to find the kernel source ...." it will offer to recreate a kernel. Accept this.
Follow the prompts as needed. Accept the system using the nVidia driver, but (at first try) do not accept reconfiguring of xorg.conf. When all is done, enter 'reboot now' and your system will restart.

If you find that your settings are still not right, which means your xorg.conf was changed during earlier tinkering, you should now be able to go to the nVidia Settings applet and reconfigure to your liking.

One of the things you should do is open xorg.conf and your renamed xorg.conf.9506 and compare them. Consider renaming xorg.conf.9506 back to xorg.conf.

Although it is possible to restart the x-server with Ctrl-Alt-Backspace, I have found that this seldom works satisfactorily. Better reboot each time until you are happy the display is what you want. If necessary. go through this several times, but each time from the command prompt through the recovery mode.

Good luck

---

