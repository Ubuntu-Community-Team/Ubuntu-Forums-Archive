---
title: "Ubuntu 9.04 Nvidia driver failure to create xorg.conf correctly"
date: 2009-06-01
forum: General Help
---

### Post by shuffman37 on 2009-06-01
I just did multiple tries installing 9.04 and everytime I enable any of the listed Nvidia drivers in restricted drivers I end up with a blank screen at log in. I had it working with the nvidia driver by copying my xorg.conf from my working 8.10 install and replaced the one nvidia made in 9.04. But after I rebooted same problem. I used the recovery thing (xfix) to be able to log in again and after that I tried my Xorg.conf from 8.10 again and that did not work. Everytime I've ran "sudo nvidia-xconfig" it makes the same xorg file that gives me a blank screen. I've tried allthe Nvidia drivers listed and even the one from their site. Oh and I have read through everything I can find on here about it but nothing seems to work =(

---

### Post by shuffman37 on 2009-06-02
Yay, I've got it working now! I had to reinstall the system and completely update everything before it would work and I had to install "dkms" (Dynamic Kernel Module Support Framework) and then the nvidia driver made a working xorg.conf. If anyone needs a working basic nvidia driver xorg file here is a copy of mine. 

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by David Crockett on 2009-06-03
Good for you.  I have the same set of problems.    How do I installl DKMS?  

How do I run sudo nvidia-xconfig?   All I get is bad command?  What am I doing wrong?   I went to the terminal and ran the line and then i was asked for my password.  I gave my password and then all I got is bad command message.   Please help.

D

---

### Post by shuffman37 on 2009-06-04
To install DKMS just open up Synaptic and search for it under all packages. Once you do that and completely update your system you should be able to enable your driver with "restricted drivers application". That should set up the Xorg.conf correctly after you have updated everything and installed DKMS. If that doesn't set up the Xorg.conf corecctly open your file manager as root, replace the xorg.conf lines with mine if your using the 180.44 nvidia driver and you should have a working setup. If that fails boot into recovery mode and run Xfix from the list of options. Then you can log in and try agian.

---

### Post by David Crockett on 2009-06-05
Thanks for the tips.   I have already loaded DKMS and used the driver installation utility.   When I rerun it it says that the NVIDIA driver is activated.    

How do I manually edit the xconfig file?   I have been able to read it as follows

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Thanks

---

### Post by shuffman37 on 2009-06-05
If you have the nvidia-settings tool installed (comes with the driver) you could run that as root to change the file automatically. Whats your current resolution and refresh rate? If you run Nvidia-Settings does it give you a error or anything?

---

### Post by shuffman37 on 2009-06-05
If you want to try to manually edit it (back it up and use caution!) you can type in "sudo nautilus" then in the root file manager go to the xorg.conf, open it with text editor and make your changes.

---

### Post by David Crockett on 2009-06-06
Hi,

Thank you for the reply.  I will try this Monday.  My Ubuntu computer is in my laboratory.  

Best wishes,
David

---

