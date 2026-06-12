---
title: "kde wont start"
date: 2005-07-18
forum: Desktop Environments
---

### Post by matva on 2005-07-18
Yesterday i made the mistake of updating my system with kynaptic (i checked for updates and updated all). When i restarted, kde didn't start. I get:

hald.c:302:Your kernel does not support capabilities. 

the nvidia screen no longer comes up. What happened? Is there any way to revert back? 

I can login under the command, but thats it.

---

### Post by mad_scientist03 on 2005-07-19
When you log in using the terminal, try "startx" to see if the graphical display kicks in. If it does, great. If not, you will likely be pointed to "/var/log/Xorg.0.log" for more information. You can then try a "sudo dpkg-reconfigure xserver-xorg" to reconfigure your graphical display. Sometimes the reconfiguration process will cleanse your system of any bad settings it developed or will align the settings better with any new packages you have installed since the original configuration.

---

### Post by ghoshe on 2005-07-19
It seems that the update changed your kernel image, try to reinstall the nvidia drivers, but purge before your old configuration, try (sudo):

         apt-get remove --purge nvidia-glx-driver
         apt-get install nvidia-glx-driver
         nvidia-glx enable (i can't remember if this the correct expression)

I had a similar problem a few months ago. Now i'm a happy ati radeon owner ;-) .

Good Luck.

---

