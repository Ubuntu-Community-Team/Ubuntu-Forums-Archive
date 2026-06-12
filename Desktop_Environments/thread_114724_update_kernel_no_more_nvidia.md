---
title: "update kernel no more nvidia"
date: 2006-01-09
forum: Desktop Environments
---

### Post by errr on 2006-01-09
Hi, Im pretty new to ubuntu and followed this [http://help.ubuntu.com/starterguide/C/ch04.html#installnvidiadriver](http://help.ubuntu.com/starterguide/C/ch04.html#installnvidiadriver) got nvidia all working and then noticed I had some update waiting for me (it was a kernel update) so I did it, then rebooted, and had to switch my driver back to nv to get in X. I then reinstalled the nvidia-glx and even reinstalled the Non-free Linux 2.6.12 modules on 386 and the nvidia-settings still no nvidia. I then did ```
sudo dpkg-reconfigure xserver-xorg
``` and selected nvidia in that process, and verified that it was nvidia and not nv but still no nvidia.. What else can I do.. When I was on gentoo and updated my kernel I just had to reinstall the driver and then update opengl.. Im lost on what to do for this.. any suggestions??

---

### Post by Gowator on 2006-01-09
[QUOTE=errr]Hi, Im pretty new to ubuntu and followed this [http://help.ubuntu.com/starterguide/C/ch04.html#installnvidiadriver](http://help.ubuntu.com/starterguide/C/ch04.html#installnvidiadriver) got nvidia all working and then noticed I had some update waiting for me (it was a kernel update) so I did it, then rebooted, and had to switch my driver back to nv to get in X. I then reinstalled the nvidia-glx and even reinstalled the Non-free Linux 2.6.12 modules on 386 and the nvidia-settings still no nvidia. I then did ```
sudo dpkg-reconfigure xserver-xorg
``` and selected nvidia in that process, and verified that it was nvidia and not nv but still no nvidia.. What else can I do.. When I was on gentoo and updated my kernel I just had to reinstall the driver and then update opengl.. Im lost on what to do for this.. any suggestions??[/QUOTE]
What does your 
/etc/X11/xorg.conf 
say for driver? nv or nvidia?

---

### Post by errr on 2006-01-09
nv, if I use nvidia X will not start.

---

### Post by Gowator on 2006-01-09
[QUOTE=errr]nv, if I use nvidia X will not start.[/QUOTE]
The nv is the opensource ine and nvidia the 'restricted' one.
If you look in /var/log/Xorg.0.log it should say why it failed to start .. when doing this I tend to jusr have two entries one commented out 

Driver "nv"
#Driver "nvidia"

and just switch the # round and resave then you get a GUI back to help debug what went wrong and give internet access etc.  

Its usually near the end of the file if its a fatal error so have a look and post the file or any suspisious bits :D

---

### Post by errr on 2006-01-09
> errr@joker:~$ grep  EE  /var/log/Xorg.0.log.old
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration. 
So now, I have removed all things I initially installed to get nvidia working, the nvidia-glx, the nvidia-settings, and [quote="errr"]I then reinstalled the nvidia-glx and even reinstalled the Non-free Linux 2.6.12 modules on 386 and the nvidia-settings still no nvidia. I then did ```
sudo dpkg-reconfigure xserver-xorg
```  and selected nvidia in that process, and verified that it was nvidia and not nv but still no nvidia..[/quote] I removed and reinstalled, I did complete removal of them and still no nvidia. So there has to be a simple answer for this, When you update your kernel and nvidia breaks, what do you do to fix it???

---

### Post by errr on 2006-01-09
*************SOLVED*******************************

Simply reboot, or better just ```
sudo modprobe nvidia
``` and then ```
sudo nvidia-glx-config enable
``` if like me you had set X to use nv so you could get in X, and then ```
ctrl+alt+bckspc
``` to restart the X server and get that nvidia driver loaded up.

---

