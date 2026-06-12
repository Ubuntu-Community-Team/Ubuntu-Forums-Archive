---
title: "nvidia 173.14.36?"
date: 2013-01-06
forum: Desktop Environments
---

### Post by Mia1990 on 2013-01-06
ok i am trying to install the nvidia 173.14.36 but it isn't in the software center and the  nvidia 173.14.35 won't install is there some way to install this driver if not it's not a problem as it's a old pc that I’m going to give away installing 12.10 isn't really necessary.

---

### Post by UltimateCat on 2013-01-06
By Nvidia 173.14.36 do you mean a brand new card or so you mean install the driver?

If 'Nvidia 173.14.36 is a driver and you have that driver sitting on your desktop on in your downloads directory just install it-

Open the terminal and run:
```

apt-get install <name of driver>

```
If the terminal tells you something like command not found it is because you must perform this task as 'root' ; put in your sudo password

This Ubuntu page should help:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

HTH

---

### Post by Us3r Unfriendly on 2013-01-06
Don't give up...what card do you have.  Nvidia is still providing drivers, even after the Torvolds incident hehe

---

### Post by Mia1990 on 2013-01-06
The card is a fx5500 with 256 mb of ram on it and the system has 2gb.

---

### Post by Calinou on 2013-01-06
Elaborate please? "won't install"? You should see a list of proprietary drivers in "Software Sources".

---

### Post by Mia1990 on 2013-01-06
the Nvidia driver doesn't even show up in additional drivers i go to the software center and install synaptic then look for the nvidia 173.14.36 and it's not there only the 173.14.35 and it will not install from synaptic or the software center. 173.14.36 is the newest on the nvidia website and they tell me that's what i should be using for Ubuntu 12.10 not the 173.14.35.

---

### Post by Us3r Unfriendly on 2013-01-07
cd ~/Downloads/

wget [http://us.download.nvidia.com/XFree86/Linux-x86/304.64/NVIDIA-Linux-x86-304.64.run](http://us.download.nvidia.com/XFree86/Linux-x86/304.64/NVIDIA-Linux-x86-304.64.run)

...this is for a 32 bit Linux

wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/304.64/NVIDIA-Linux-x86_64-304.64.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/304.64/NVIDIA-Linux-x86_64-304.64.run)

...this one is for a 64 bit version of Linux

open nautilus to the run file and right click it and make it "allow executing file as program", then run it via double clicking the run file or use the terminal to run it.

---

