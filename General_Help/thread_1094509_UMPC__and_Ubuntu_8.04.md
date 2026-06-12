---
title: "UMPC  and Ubuntu 8.04"
date: 2009-03-12
forum: General Help
---

### Post by vanixtopooh on 2009-03-12
I downloaeded additional drivers for my UMPC Laptop w/c is
unichrome.83-242-u804.tar on my desktop and followed this step by step but can't go further
the steps are attached into the driver w/c I download
here it is

This driver is for Ubuntu 8.04 LTS Desktop Edition.

Installation and Uninstallation
===============================
1. How to Install/Uninstall the via Linux Driver
1.1 uncompress the via driver package
tar zxvf ./unichrome.83-242-u804.tar.gz
1.2 Install the via linux driver
cd ./unichrome.83-242-u804
sudo ./vinstall
Reboot system
1.3 Uninstall the via linux driver
cd ./unichrome.83-242-u804
sudo ./unvinstall
Reboot system

Notes
=====
2. How to enable 3D desktop effects
2.1 edit the script file /usr/bin/compiz, find the line:
WHITELIST="nvidia intel ati radeon i810"
2.2 modify it to:
WHITELIST="nvidia intel ati radeon i810 via"
2.3 restart x-server ("Ctl+Alt+Backspace) after "./vinstall" and reboot finished

and following the steps w/c cant go further

here it is

rhoel@rhoel-laptop:~$ tar zxvf Desktop/unichrome.83-242-u804.tar.gz
unichrome.83-242-u804/
unichrome.83-242-u804/bin/
unichrome.83-242-u804/bin/via.ko
unichrome.83-242-u804/bin/via_drv.so
unichrome.83-242-u804/bin/libGL.so.1.2.via_unichrome
unichrome.83-242-u804/bin/via_unichrome_dri.so
unichrome.83-242-u804/viax.conf
unichrome.83-242-u804/README
unichrome.83-242-u804/vinstall
unichrome.83-242-u804/vuninstall
unichrome.83-242-u804/Release_notes.txt
rhoel@rhoel-laptop:~$ cd Desktop/unichrome.83-242-u804
bash: cd: Desktop/unichrome.83-242-u804: No such file or directory
rhoel@rhoel-laptop:~$ cd Desktop/unichrome.83-242-u804
bash: cd: Desktop/unichrome.83-242-u804: No such file or directory
rhoel@rhoel-laptop:~$ cd Desktop/unichrome.83-242-u804
bash: cd: Desktop/unichrome.83-242-u804: No such file or directory
rhoel@rhoel-laptop:~$ cd Desktop/unichrome.83-242-u804
bash: cd: Desktop/unichrome.83-242-u804: No such file or directory
rhoel@rhoel-laptop:~$ cd Desktop./unichrome.83-242-u804
bash: cd: Desktop./unichrome.83-242-u804: No such file or directory
rhoel@rhoel-laptop:~$ cd Desktop/unichrome.83-242-u804
bash: cd: Desktop/unichrome.83-242-u804: No such file or directory
rhoel@rhoel-laptop:~$ cd ~/Destop/unichrome.83-242-u804
bash: cd: /home/rhoel/Destop/unichrome.83-242-u804: No such file or directory
rhoel@rhoel-laptop:~$


am I doing something wrong here or am I missing..
I do installed the build essential via synaptic but how come ????

and I still don'y get it what does ./ means???

---

