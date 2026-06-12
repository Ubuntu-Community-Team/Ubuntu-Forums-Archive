---
title: "[SOLVED] Error When Trying to Install nVidia drivers"
date: 2008-01-11
forum: Desktop Effects &amp; Customization
---

### Post by ataxicwolf on 2008-01-11
So I've been trying to update my Nvidia drivers so that I can use some cool desktop stuff. The first problem arose when I tried to install it based off the drivers I downloaded from the nvidia site. I booted into 'Single' user mode, then did the install with "sh [driver name]", but when it came up with the installer, it first told me it might have problems since I was in runlevel 1, but I told it to ignore it (I didn't know what else to do :() It then told me it would have to compile it's own stuff, which I OK'd. Then, it came up with the error message like "Error: You don't have libd (or something, I don't really remember) headers installed. Please install the headers to continue with the intsallation"

After this error, I decided to follow the directions from this site:
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

After I followed it's directions with installing the nvidia drivers, xorg won't even start!

So I'm really hoping someone else on the Ubuntu forums knows how to fix this, cause I'm really lost, and even worse, a brand new Ubuntu noob. 

Thanks for any help you guys can give me, I really hope I can fix this!

Stephen

---

### Post by overdrank on 2008-01-11
> **ataxicwolf said:**
> So I've been trying to update my Nvidia drivers so that I can use some cool desktop stuff. The first problem arose when I tried to install it based off the drivers I downloaded from the nvidia site. I booted into 'Single' user mode, then did the install with "sh [driver name]", but when it came up with the installer, it first told me it might have problems since I was in runlevel 1, but I told it to ignore it (I didn't know what else to do :() It then told me it would have to compile it's own stuff, which I OK'd. Then, it came up with the error message like "Error: You don't have libd (or something, I don't really remember) headers installed. Please install the headers to continue with the intsallation"

After this error, I decided to follow the directions from this site:
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

After I followed it's directions with installing the nvidia drivers, xorg won't even start!

So I'm really hoping someone else on the Ubuntu forums knows how to fix this, cause I'm really lost, and even worse, a brand new Ubuntu noob. 

Thanks for any help you guys can give me, I really hope I can fix this!

Stephen

HI and  you can try and boot into recovery mode which is usually the second choice in the grub. The reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` or startx and hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by ataxicwolf on 2008-01-11
thanks very much overdrank!
This worked perfectly and I am now up and running.

Does anyone know how I should install the new nvidia drivers?

---

### Post by ataxicwolf on 2008-01-11
Alright, so I've looked at the Nvidia README for the drivers, and I think I know what the problem is. According to nVidia:

> On most systems, this means that you will need to locate and install the correct kernel-source, kernel-headers, or kernel-devel package

So I need to install the kernel-source, kernel-headers, or the kernel-devel package, how am I supposed to do this?

Thanks for the help!

---

### Post by overdrank on 2008-01-11
> **ataxicwolf said:**
> Alright, so I've looked at the Nvidia README for the drivers, and I think I know what the problem is. According to nVidia:



So I need to install the kernel-source, kernel-headers, or the kernel-devel package, how am I supposed to do this?

Thanks for the help!

HI and I have to ask, Have you tried the restricted drivers? Located under system, administration.

---

### Post by ataxicwolf on 2008-01-11
It claimed that my hardware did not need any restricted drivers when I tried it.

---

### Post by overdrank on 2008-01-11
> **ataxicwolf said:**
> It claimed that my hardware did not need any restricted drivers when I tried it.

Ok what is the model of the graphics card, you can use the command lspci  and look for VGA:

---

### Post by ataxicwolf on 2008-01-11
The output of lspci for VGA: is this:

nVidia Corporation Unknown device 0402 (rev a1)

The model of the card is an Nvidia 8600GT

---

### Post by overdrank on 2008-01-11
> **ataxicwolf said:**
> The output of lspci for VGA: is this:

nVidia Corporation Unknown device 0402 (rev a1)

The model of the card is an Nvidia 8600GT

Ok if you would like you can use this command to update your pci icds
```
sudo update-pciids
```
As for the drivers it is hard to believe it say you don't need any drivers but I would recommend Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ataxicwolf on 2008-01-11
it seems that the installation went perfectly :)

Thanks so much for your time and help overdank, I couldn't have done it without ya.

---

### Post by overdrank on 2008-01-11
> **ataxicwolf said:**
> it seems that the installation went perfectly :)

Thanks so much for your time and help overdank, I couldn't have done it without ya.

No problem and glad to be of some help. Good luck and enjoy, please mark the thread as solved, underneath thread tools. :KS

---

