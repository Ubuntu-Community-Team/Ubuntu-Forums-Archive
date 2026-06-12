---
title: "Exiting X Server and terminating all OpenGL applications?"
date: 2008-06-06
forum: Desktop Environments
---

### Post by br0ken on 2008-06-06
I am trying to install NVIDIA-Linux-x86-173.14.05-pkg1.run so i will have drivers for the NVIDIA GeForce 7300LE, and i need to terminate the X Server and since i am quite new to linux, i haven't been able to do this yet. I logged out and tried to change my session to failsage terminal but that still ran X Server. Any help would be greatly appreciated and so far I've seen *kbunt has an AMAZING amount of people more than willing to help others whenever possible :) thanks!

---

### Post by Nythain on 2008-06-06
control+alt+f1
login
sudo /etc/init.d/gdm stop

that should effectively kill your xsession, just be sure to do it from a tty and not a terminal emulator :)

---

