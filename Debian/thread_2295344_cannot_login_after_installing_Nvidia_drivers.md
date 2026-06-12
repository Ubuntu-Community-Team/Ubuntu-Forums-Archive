---
title: "cannot login after installing Nvidia drivers"
date: 2015-09-17
forum: Debian
---

### Post by Zombir on 2015-09-17
Hi,


I'm new to Debian and installed it with Cinnamon because I want to learn some OpenCL programming in Linux. I have a Nvidia GT 525M GPU. Once the operating system is installed, I followed [https://wiki.debian.org/NvidiaGraphicsDrivers](https://wiki.debian.org/NvidiaGraphicsDrivers) article to install the proprietary Nvidia drivers. As the forum suggested, instead of creating an Xorg server configuration file, I installed Bumblebee according to [https://wiki.debian.org/Bumblebee](https://wiki.debian.org/Bumblebee) article. 


But when I restarted my machine after completing all the steps when I try to log in I get the follwoing message:


"failed to load session 'cinnamon'"


I cannot login as normal user or root. 


Please help. 
Thank you
PPG

---

### Post by arochester on 2015-09-19
Try going into a virtual terminal by pressing Alt+Ctrl+F1. 

If you can do that

a) Type:  startx   Do you get any error messages?

b) If X doesn't start try reinstalling cinnamon.  Input: su to become Root, then: apt-get install cinnamon

c) Try installing a different Desktop Environment/Windows Manager e.g. Fluxbox . Input: su to become Root, then: apt-get install fluxbox  ---then startx

---

