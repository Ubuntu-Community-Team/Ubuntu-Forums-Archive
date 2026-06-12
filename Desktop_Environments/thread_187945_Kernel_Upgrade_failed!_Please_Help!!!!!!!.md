---
title: "Kernel Upgrade failed! Please Help!!!!!!!"
date: 2006-06-03
forum: Desktop Environments
---

### Post by bobby19 on 2006-06-03
My system:
Intel Pentium 3
360 mb ram 
Ubuntu 5.10

 I know I am in the Dapper forums instead of the breezy forums, but I need someone to help me fast. Using the synaptic package manager, I thought I could get better performance if I installed the 686 kernel becuase I had the 386. I installed it and it said it was installed correctly. I then rebooted to see if everything was alright, it wasn't. Right before I got to the login screen, the command prompt kept comming up and saying Ubuntu login. After waiting a few seconds, it went to a screen with all garbeled graphics on it, saying that the X server isn't configured properly. I clicked ok and it took me back to the black screen with Ubuntu login. For the record, I have an nvidia geforce 2 graphics card and I had to install the nvidia glx legacy driver prior to the kernel install because I was getting frequent crashes. I think that maybey because the driver is legacy and not new, the x server isn't starting with the new kernel. Could this be the case and if so how could I fix this or atleast revert back to the 386 kernel. I would normaly just reinstall everthing with the cd, but I have important documents that I need  ](*,) , please help! Thank you.

---

### Post by hod139 on 2006-06-03
Try installing the restricted modules for your kernel which will contain the driver
```
sudo apt-get install linux-restricted-modules-686
```
and then reboot

---

### Post by sgbeamer on 2006-06-03
You should be good to go if you just reboot (CTRL-ALT-DEL) and look for your old kernel on the Grub menu when the computer initially boots.  You will have to manually select it in the 5 - 10 seconds before the new default kernel installs.  You can modify grub from where you are by going to /boot/grub/ and editing the file menu.lst to pick a different kernel to boot from by looking for a line that says default=0 and changing it to the one you want from the list at the bottom of the file.   Grub starts counting at 0 so #1=0, 2=1, etc.

---

