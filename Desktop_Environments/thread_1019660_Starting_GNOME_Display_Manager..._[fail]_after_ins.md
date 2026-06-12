---
title: "Starting GNOME Display Manager... [fail] after installation nvidia driver"
date: 2008-12-23
forum: Desktop Environments
---

### Post by crazyheinz on 2008-12-23
Hi? I installed a the newest nvidia driver to be able to run cuda on ubuntu. I followed the guide but now i can't get gnome to work anymore. I've tried to run ```
sudo /etc/init.d/gdm 
```start but that gives the error in the topic title. But the weird part is that i only get that error in recovery mode, in normal mode it's ```
Starting GNOME Display Manager... [ok]
```
What can i do?

sudo aptitude install ubuntu-desktop doesn't work cause i have wireless internet that not automatically connects to the network.

---

### Post by gettinoriginal on 2008-12-23
I am not a guru, but at the log in window, options, choose gnome and then log in. (:confused:)

---

### Post by s3gfault on 2008-12-23
You'll want to check the logfile for X for error messages, it should be in /var/log.  Once you find the error message then you will have more information for your troubleshooting.  Probably some of the parameters are illegal for the new driver.

You can also try reconfiguring X, i believe the command is dpkg-reconfigure x11-common.

---

### Post by crazyheinz on 2008-12-25
when i do the reconfigure thing it asks for a 'nice value'; i enter 0 and press enter, but after that it does nothing. 
How can i vieuw the log file, i have only commandline.

---

