---
title: "nvidia-xconfig not found?"
date: 2011-05-12
forum: Desktop Environments
---

### Post by redocpot on 2011-05-12
I'm running 10.04 .

I was having issues with the nvidia driver, and in the process
of adding/removing packages, I seem to have lost the binary "nvidia-xconfig".
Every set of instructions out there says "run nvidia-xconfig",
but I can't seem to find the dang binary! I've searched
synaptic, etc. to no avail.

Which package provides "nvidia-xconfig" ?? Can somebody please
point me to it??

This is very frustrating.

---

### Post by mikewhatever on 2011-05-12
There is no such package in the repositories. I believe it's part of the proprietary driver, so install the driver first, then run nvidia-xconfig.

---

### Post by redocpot on 2011-05-12
But I have "nvidia-current" and "nvidia-settings" installed.

From what I have read, I just need to do the following
to get the nvidia driver working:

> sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

I have tried the above, and I keep getting the error:
Failed to load module "nvidia": module does not exist

---

### Post by redocpot on 2011-05-13
After trying every combination of nvidia packages around, I gave up and downloaded the driver from NVidia directly.

One command, "./NVIDIA-Linux....run", and I was all set.

---

### Post by fagulhaspt on 2012-03-16
The same happened to me... while trying to uninstall the nvidia drivers, I inadvertadly uninstalled more than I should, and lost the "nvidia-xconfig" command...

After searching like a crazy, it got fixed, although I don't know exactly what was the package that got it back.

What I did in the process was:
```
 sudo apt-get install nvidia-va-driver
 sudo apt-get install libva-glx1
 sudo jockey-gtk
 # and installed the proprietary nvidia drivers
 # reboot
 # and I then noticed that I got back nvidia-xconfig
```

so some of these must have fixed it... libva-glx1 is not probably the one, so that leaves **nvidia-va-driver** as the main suspect 

Hope it helps someone who falls into such a deep hole as I was :)


**NOTE:** this gets cloudier, but an explanation surely exists
   I found [this article]("http://www.ubuntugeek.com/what-package-is-that-file-in.html") explaining how to discover which deb-package contains a specific file.
   So I used it, and found that "nvidia-xconfig" comes inside the package "nvidia-current"
   The thing is that I already had that package installed and even so "nvidia-xconfig" was not available... maybe "nvidia-xconfig" is only installed if some conditions are met,don't know...
   Although I apport no clarity to the solution of the question, I hope someone can unriddle all this, for the benefit of others :)

**PS:**
  The correct way to install nvidia drivers in ubuntu is explained here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") So if you don't mess around before reading this (as I did) you will probably be just fine, and everything will work out nicely

Greetings

---

