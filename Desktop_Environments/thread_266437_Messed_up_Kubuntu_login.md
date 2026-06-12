---
title: "Messed up Kubuntu login"
date: 2006-09-27
forum: Desktop Environments
---

### Post by jqp on 2006-09-27
I decided that I wanted to use KDE instead of Gnome in Ubuntu, so I installed the KDE-related packages in apt-get.  As part of that process is installed the kdm login screen and that's what I use to log in now.  I just did all this yesterday.

Now, when I try to login, I type in my username and password.  The screen goes blank for a few seconds and then I end up back at the login screen.  I really don't know what's going on there.  It happens whether I try "Change Session" to either KDE or GNOME.

I was able to figure out how to get to a failsafe terminal and start gdm with "sudo gdm", and then from gdm, I could log in to either GNOME or KDE without any problem.  That's how I'm logged in now, but when I reboot the computer, I end up back at the kdm screen and I have the same problem.  

Any suggestions?

---

### Post by ajgreeny on 2006-09-27
Sounds like your kdm is borked or something similar.  In a terminal or using the console login do:-
sudo dpkg-reconfigure kdm
This will let you change back to gdm which may work OK.  Best of luck with that, and if it works you could then try again by completely uninstalling kdm including the .deb file in /var/cache/apt/archives, and then reinstall with apt-get, synaptic or aptitude.

---

### Post by jqp on 2006-09-27
It didn't work =(

I did successfully switch to gdm as the default by using 
sudo dpkg-reconfigure kdm 

Then, I used synaptic to remove kdm and kubuntu-desktop (which depends on kdm).  Next, I removed teh kdm deb file from /var/cache/apt/archives as you said.  Then, I rebooted, and I logged in using gdm.  Next, I used Synaptic to instlal kdm and kubuntu-desktop.  After that, I rebooted and tried to log in with kdm.  Same results as before.

Now that I think about it, I think I click "Mark for Removal" instead of "Mark for Complete Removal" on both of those packages.  Could have have been my problem?  If so, I'll try again tomorrow.  

Also, is there a way to get to GNOME configuration window for GDM from within KDE?  If I'm going to use KDE and GDM, I guess I need a way to configure GDM from within KDE.

Thanks for the help

---

