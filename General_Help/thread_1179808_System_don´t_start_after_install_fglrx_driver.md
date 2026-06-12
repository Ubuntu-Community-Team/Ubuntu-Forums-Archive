---
title: "System don´t start after install fglrx driver"
date: 2009-06-06
forum: General Help
---

### Post by Hedberg on 2009-06-06
Hello all of you kind people. I´ve made an persistant install of Ubuntu 9.04 on a USB-stick. After some time of configuration i decided to install the fglrx driver for my ATI radeon card as well as the ATI Catalyst control center. After reboot, I choose "run persistantly" and Ubuntu doesn´t start. All that happens is that the picture gets strange. Anyone here who have had the same problems?

Ulf

---

### Post by uberlube on 2009-06-06
have u installed the ati drivers before u installed fglrx?

---

### Post by Hedberg on 2009-06-06
I used the pre-packaged driver install from ubuntu. Then I installed the catalyst control center.

Ulf

---

### Post by uberlube on 2009-06-06
If u mean that you just used the driver actively in use after install or the one available in the restricted driver manager then that could be why it got all messed once u installed fglrx. U should install the driver using envyNG, reboot, then install everything else.

---

### Post by Hedberg on 2009-06-06
Ok. An amateur as i am i never knew. Do you think there is a way to fix the problem without reinstalling the system?

---

### Post by Legace on 2009-06-06
> **Hedberg said:**
> Ok. An amateur as i am i never knew. Do you think there is a way to fix the problem without reinstalling the system?

Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

