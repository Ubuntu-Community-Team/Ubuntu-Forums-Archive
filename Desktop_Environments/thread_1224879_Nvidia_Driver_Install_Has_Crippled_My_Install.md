---
title: "Nvidia Driver Install Has Crippled My Install"
date: 2009-07-27
forum: Desktop Environments
---

### Post by therocco2k on 2009-07-27
Im Running Ubuntu 9.04 - I Downloaded the driver for my geforce 8800gs graphics card from the nvidia site and followed the instructions. Opened a Terminal while in my desktop and typed sh NVIDIA-Linhx-x86-185.18.14-pkg1.run. It told me I had to be outside the X Desktop environment.

I Looked up how to get out of the x environment and found a site told me to go to System>Administration>Serivces and uncheck Graphic Login Manager (GDM). I did and the system rebooted into a Terminal.

I Ran the installation code, it worked, then it said that the system doesnt have a kernel and would you like nvidia to build a kernel for you. I hit ok, then it asked me if I want it to automatically confirgure the CONFIG file for me, I Accepted, it ran and appeared to work, said installation was finished and took me back to the Terminal.

I Typed startx - Then I got error that I dreaded. - It wouldn't start the graphical GDM. I forgot the error messages it said but there were a few and it wouldn't load the system back up.

I Rebooted and selected ubuntu  (recovery mode) and it let me log in (no graphical login screen though) - I rebooted again, and I selected normal ubuntu and it loaded it up. 

Now my 3D app's wont even work (3D Chess, Etc .. and for some reason i got an error that said "User Switcher" has quit unexpectedly If you reload a panel object, it will automatically be added back to the panel. I hit reload and it returns same error.


I'm Stuck - Im new to Linux so I have no idea what to do, if I could return to the state I was at before I tried to install the Nvidia Graphics Driver That would be More than OK. I Dont need that driver installed that bad, everything was just fine without it.

Is there anyway to fix my Linux Install? I would like to do some type of System restore or anything to REMOVE the stupid Nvidia Driver and Get back to how it was before I installed the driver.

Please - Somebody help, I Really am in LOVE with my linux OS and this might force me to Uninstall Linux and stick with windows or reinstall Linux and lose everything I've worked for up to this far..

Help - Please.:confused:

---

### Post by Arup on 2009-07-27
If you wish to install via .sh, make sure you have purged linux restricted modules and also purged nvidia* otherwise all these issues you mention will crop up, the built in one from repos can't exist with drivers installed via .sh

---

### Post by therocco2k on 2009-07-27
I Appreciate your reply, but that is what I Should not have done. Now I'm stuck with not being able to start my computer with Ubuntu Normal Boot, Only (Recovery Mode), and even then, I don't get a Login Screen - I have to login via terminal and then type startx

I Absolutly NEED Ubuntu's Default Grapics Driver re-installed and this problem fixed because I use Ubuntu to Develop 3D Applications.

This is such a problem for me that I'm really frustrated and don't know wha tto do.

Is there any way to REVERSE what I did, or UNINSTALL the Nvidia Drivers I Tried to install and return my system to normal? 

I don't mean to sound desprate but computers is my life - I use computers for my Carrer, if I cannot get this problem fixed I will be in knee deep.

If anybody can help me I'd Greatly Appreaciate it, Thank you for taking the time to read my problem and if you can, thank you for taking the time to help me fix it.

RVC - Ninja-Development

> **Arup said:**
> If you wish to install via .sh, make sure you have purged linux restricted modules and also purged nvidia* otherwise all these issues you mention will crop up, the built in one from repos can't exist with drivers installed via .sh

---

### Post by philcamlin on 2009-07-27
boot into recovery go to console
and purge

---

