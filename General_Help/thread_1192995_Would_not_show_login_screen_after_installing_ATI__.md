---
title: "Would not show login screen after installing ATI  driver in ubuntu 9.04"
date: 2009-06-20
forum: General Help
---

### Post by kraddark on 2009-06-20
Hi All!

I've installed ATI driver in ubuntu 9.04.. After installing it, ubuntu won't show the login screen or if it will, it's garbled and I can't do anything.. I tried going to recovery mode and select fix display errors but it didn't do anything.

I'm on dual boot with XP.


Any ideas would be perfect. thanks!:(

---

### Post by x33a on 2009-06-20
how did you install the drivers, through synaptic, apt, or some shell script?

---

### Post by kraddark on 2009-06-21
> **x33a said:**
> how did you install the drivers, through synaptic, apt, or some shell script?

downloaded the file then did it via terminal

---

### Post by Legace on 2009-06-21
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

Then, follow this guide to manually install the drivers:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

---

### Post by kraddark on 2009-06-21
> **Legace said:**
> Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
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

Then, follow this guide to manually install the drivers:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

that's exactly what i did which caused this issue to happen..:(

---

### Post by Legace on 2009-06-21
> **kraddark said:**
> that's exactly what i did which caused this issue to happen..:(

Did you try to uninstall those drivers as I mentioned above?

---

### Post by kraddark on 2009-06-21
> **Legace said:**
> Did you try to uninstall those drivers as I mentioned above?

I'm sorry sir I mean uninstalling the drivers did work for me! thanks!:popcorn: what i meant is that the instructions for installing the ATI driver caused this issue.. can you help me in uninstalling the ATI driver? 

BTW: I have ATI Radeon X1650PRO

---

### Post by Yellow Pasque on 2009-06-21
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get --reinstall install libgl1-mesa-glx
```

EDIT: THe Radeon X1650 is not supported by proprietary drivers after Catalyst 9-3: [http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

---

### Post by kraddark on 2009-06-21
> **Temüjin said:**
> ```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get --reinstall install libgl1-mesa-glx
```

EDIT: THe Radeon X1650 is not supported by proprietary drivers after Catalyst 9-3: [http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

Thanks for the reply.. actually I've already resolved the part about the login screen.. now, my main issue is: how to install the ati driver

BTW: I have ATI Radeon X1650PRO

---

### Post by Yellow Pasque on 2009-06-21
The open-source ati driver comes pre-installed. THe proprietary one isn't going to work for your card on Ubuntu 9.04

---

### Post by rhd on 2009-07-02
I had the exact same problem with my Radeon 8500, ;) silly me.

Thank you very much for the help!!

---

### Post by AbsolutXTR on 2009-07-21
Hmmm.. I have the exact same problem. FireGL T2 on my ThinkPad. Thought I would get the latest and greatest drivers... they say that's a good thing to do. Anyway.

I will try this and keep my fingers crossed!

Thanks!

---

