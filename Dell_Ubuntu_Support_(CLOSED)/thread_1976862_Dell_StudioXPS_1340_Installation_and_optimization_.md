---
title: "Dell StudioXPS 1340: Installation and optimization of Ubuntu 12.04 LTS 64bit"
date: 2012-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by browncharlie on 2012-05-09
Hello everyone, I have this Dell laptop with Windows 7 64bit preinstalled. I would like to double boot with 7 and in the next future to completely switch to Ubuntu 12.04 64bit.
I have managed to install Ubuntu with many difficulties and  nowI found it runs very well and my laptop performs really fast!
Anyway i have found some issue and I'm asking yout help in order to install and optimize this great OS to be fully efficient on my harware. I alwais have asked help on ubuntu IRC channel but I thouth that could be more productive to create a thread where some developer can help me to configure this OS from scratch to fit perfectly this laptop, and also I hope it could be helpfull to all the owner of my same machine.

This are the issue that I have found till now:

1) Installation from DVD or USB runs only pressing F6 and selecting "acpi=off" option, otherwise it ends in kernel panic.

2) Once installed the system won't boot in any way, maybe cause of video card problem. I can only boot following this steps: press "e" and add "nomodeset" and "acpi=off" to the boot menu voice "recovery mode" and then once in front of the menu perform a "resume normal boot"; then I face a terminal from which, after login, I give a "sudo apt-get update" and then "sudo apt-get dist-upgrade -y" After updates the computer boots without adding any option to the grub.
During this step I found that it downloads and install a driver called "Nouveau". I have to admit that i have added a repository for some nvidia driver and tryied to install a driver called "nvidia-current" from console without any result. I mention it because maybe could be helpfull.
This laptops cames with this videocard: Nvidia GeForce 9400M G + GeForce 210M. This cards runs under Hybrid-Sli. I know this technology is not supported under Ubuntu, so I would like to shut down the discrete video card which I suppose is the GeForce 210M.
I have tried this guide but with no luck. [http://luizfar.wordpress.com/2010/06/29/how-to-switch-off-xps1340-discrete-video-card-on-linux/](http://luizfar.wordpress.com/2010/06/29/how-to-switch-off-xps1340-discrete-video-card-on-linux/)

3)Plymouth splash has low res like 640x480. This laptop has an optimal resolution of 1280x800. Setting the resolution in grub configuration files ends in a text based splash.

4) Keybiard combination "Fn+right arrow" ends in kayboard and mouse button lock. Any other combination works. Fn+right up and down to set LCD brightness increase or lower the brightnes of 2 steps at time instead of 1.

Thank you very much in advance for your kind help.:popcorn:

---

### Post by browncharlie on 2012-05-09
I have found this fix for switching off the discrete video card, but don't know if it is compatible with Ubuntu 12.04 and also...don't know how to download and install it anyway :-?.

This is the link: [http://linux-hybrid-graphics.blogspot.it/2010/06/acpicall-simple-way-to-call-acpi.html](http://linux-hybrid-graphics.blogspot.it/2010/06/acpicall-simple-way-to-call-acpi.html)

Taken from this article: [http://dell-notebook-battery.org/?p=43](http://dell-notebook-battery.org/?p=43)

---

### Post by gordintoronto on 2012-05-09
This might be useful:
[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)

Also this one:
[https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2)

---

### Post by browncharlie on 2012-05-10
[QUOTE=gordintoronto;11921095]This might be useful:
[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)

Thank you. Anyway the bumblebee driver runs only unity 2d. Maybe that's because Optimus is not the same technology of Hybrid-SLI?

---

### Post by gordintoronto on 2012-05-11
Indeed.

---

