---
title: "Visual Effects problem"
date: 2009-04-25
forum: General Help
---

### Post by gambothell on 2009-04-25
Ubuntu 9.04 on HP nc6000 laptop with ATI Radeon Mobility 9600. Ubuntu 9.04 installed correctly and everything was OK. I then installed the ATI binary and everything was OK. I then turned on Visual Effects and it worked until I rebooted. Now the screen is unreadable. I tried booting into recover and using the option to fix Xorg. No go, same problem. I deleted Xorg.conf and renamed a backup that worked. Still a no go.

I need to know how to turn off Visual Effects from the command line. Please help.  Thanks

---

### Post by gambothell on 2009-04-25
Thanks to other posts, I was able to fix it.

1.  Booted into Recovery and went to command prompt.
2.  typed: apt-get remove xorg-driver-fglrx 
3.  typed: sudo dpkg-reconfigure xserver-xorg --frontend=gnome
4.  rebooted

---

### Post by gambothell on 2009-04-25
After further testing, I found out what was really causing the problem. It was NOT Visual Effects. The problem was installing the ATI Binary X.Org driver. When I got the system back up and running the Ubuntu default driver for 9.04, I could then turn on Visual Effects and it works just fine. The problem is that I still do not have video acceleration. I downloaded the most current ATI drivers for my ATI Mobility 9600 M10 card. The driver installed properly, but again after reboot the screen was garbage. I tried running the ATI command: aticonfig --initial -f but with no success.

By the way, you may not know how to remove the ATI driver. To do that hit Esc in Grub to get the menu and select Recover. Press down arrow and select menu Root. 

type: cd /usr/share/ati
make sure you are in the /usr/share/ati folder
type: sh ./fglrx-uninstall.sh then reboot

Note: Ubuntu 8.04 worked properly with my nc6000 and ATI Mobility 9600 M10 card with the ATI binaries loaded. I never got Ubuntu 8.10 to work with video card acceleration on the notebook including using the ATI cataylst drivers. It appears that Ubuntu 9.04 is also in the same boat. 

I suspect my video card is getting too old and there is little effort to support it anymore.... sigh.:(

---

