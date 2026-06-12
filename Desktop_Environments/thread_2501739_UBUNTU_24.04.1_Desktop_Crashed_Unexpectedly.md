---
title: "UBUNTU 24.04.1 Desktop Crashed Unexpectedly"
date: 2024-10-19
forum: Desktop Environments
---

### Post by AnupamMitra on 2024-10-19
The OS on one of my PCs was Ubuntu 24.04.1. Yesterday there was some  problem in Livepatch. To set the matter right I followed the guidelines  so given in  [https://github.com/snap-stanford/snap/issues/240](https://github.com/snap-stanford/snap/issues/240) and then *sudo pro enable livepatch*.


 During the period I received 2/3 messages saying “Sorry Ubuntu  24.04.1 had experienced an internal error” and I opted to send the error  report to Ubuntu. I turned off the computer after the update was finished.


 But today when I turned on the computer, after booting, a message  came on screen that “Something has gone wrong. A problem has occurred  and the system can’t recover. Please contact a system administrator.”


 What to do now? Whether I  have to install the OS afresh? Or is there  any other alternative? How do I recover my documents etc.? I do not  have any backup in any external device. Kindly guide.

---

### Post by ajgreeny on 2024-10-19
First thing to do is recover all your personal documents, files  music, videos, etc, and create that backup that you say you don't yet have! Backups are probably the most important job to be done throughout your computer life; you only miss them when you really, really need them, so get it done now!!!

Boot to a live system using the USB you used to install Ubuntu and copy all the files from the home of the installed system which should be visible in the left hand pane of the file manager, on to another external disk. Depending on the filesystem of your external disk, this may need root permissions which in the live system will not need a password but may need sudo commands. 
I don't use Ubuntu with gnome and I'm not certain these days how or if you can use a GUI in gnome to carry out this activity so wait for other replies.

Once your files are backed up safely we can try to figure out what's gone wrong and repair the filesystem or simply reinstall.

---

### Post by grahammechanical on 2024-10-19
I have received that message on one of my Ubuntu installs. In my opinion it is a message that is a stupid as the old error messages of Windows of years gone-by. I am the only user on this machine. That makes me the administrator. And I have no idea how to fix things. So, don't call me. :)

I tried Advanced options for Ubuntu and loading another Linux kernel. Then, loading a recovery mode kernel. Resume did not fix things. Then recovery menu>Network + Root shell prompt + Update + Upgrade did not change anything. Finally, recovery menu>Dpkg and that removed some many packages that the install was well and truly broken.

So, call an administrator and let him re-install Ubuntu.

Regards

---

### Post by AnupamMitra on 2024-10-20
> **ajgreeny said:**
> First thing to do is recover all your personal documents, files  music, videos, etc, and create that backup that you say you don't yet have! Backups are probably the most important job to be done throughout your computer life; you only miss them when you really, really need them, so get it done now!!!

Boot to a live system using the USB you used to install Ubuntu and copy all the files from the home of the installed system which should be visible in the left hand pane of the file manager, on to another external disk. Depending on the filesystem of your external disk, this may need root permissions which in the live system will not need a password but may need sudo commands. 
I don't use Ubuntu with gnome and I'm not certain these days how or if you can use a GUI in gnome to carry out this activity so wait for other replies.

Once your files are backed up safely we can try to figure out what's gone wrong and repair the filesystem or simply reinstall.

Thanks Ajgreeny for your cooperation. I did it as per your advice and now everything is okay.

---

### Post by AnupamMitra on 2024-10-20
> **grahammechanical said:**
> I have received that message on one of my Ubuntu installs. In my opinion it is a message that is a stupid as the old error messages of Windows of years gone-by. I am the only user on this machine. That makes me the administrator. And I have no idea how to fix things. So, don't call me. :)

I tried Advanced options for Ubuntu and loading another Linux kernel. Then, loading a recovery mode kernel. Resume did not fix things. Then recovery menu>Network + Root shell prompt + Update + Upgrade did not change anything. Finally, recovery menu>Dpkg and that removed some many packages that the install was well and truly broken.

So, call an administrator and let him re-install Ubuntu.

Regards

Thanks grahammechanical. As suggested by ajgreeny yesterday, through a bootable USB I recovered all my documents first and thereafter simply reinstalled the OS.

---

