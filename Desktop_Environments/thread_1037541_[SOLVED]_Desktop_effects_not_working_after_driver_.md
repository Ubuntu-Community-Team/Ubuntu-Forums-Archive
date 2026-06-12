---
title: "[SOLVED] Desktop effects not working after driver troubles"
date: 2009-01-11
forum: Desktop Environments
---

### Post by risingpowers on 2009-01-11
I installed the 180.22 Nvidia driver without first removing the 177 one. After I realized that this was a problem, I uninstalled all Nvidia drivers on the system, rebooted, then installed the 177 driver again through Hardware Drivers. I get the correct resolution, but I cannot enable desktop effects anymore. How can I enable my desktop effects?

---

### Post by gettinoriginal on 2009-01-11
System > Admin > Hardware Drivers, let it select the correct driver and enable it, then System > Preferences > Appearance > Visual Effects should be set to Extra or Custom.  
Lastly, copy paste in terminal:
```
compiz --replace
```

---

### Post by risingpowers on 2009-01-11
> **gettinoriginal said:**
> System > Admin > Hardware Drivers, let it select the correct driver and enable it, then System > Preferences > Appearance > Visual Effects should be set to Extra or Custom.  
Lastly, copy paste in terminal:
```
compiz --replace
```

The problem is that I can't set the visual effects to anything. Also, this is what I got when I typed in compiz --replace:

```
zachary@zachary-ubuntu-PC:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by risingpowers on 2009-01-11
Bump.

---

### Post by gettinoriginal on 2009-01-11
Do you have "ubuntu-restricted-extras" and "linux-restricted-modules" installed ??  They are in Synaptic.

---

### Post by sofasurfer on 2009-01-11
I am having the same problem and so far I am not getting any helpful solutions. Check out my last couple of posts in other threads to see if any progress is made.

---

### Post by gettinoriginal on 2009-01-12
I am not clear on something from either of you, and it is my confusion, so please forgive me.  Under System > Admin > Hardware Drivers, does it show that your driver is enabled ??

---

### Post by cb34 on 2009-01-12
look into your /etc/X11/xorg.conf file for some problems is my first guess.
----

what i do is remove ALL nvidia packages in synaptic.. purge.
anything with the name nvidia in it.

then download the nvidia driver from nvidia's site. (or do this first..whatever..)

then CTRL-ALT-F1, login..

sudo /etc/init.d/gdm stop (need to stop the graphic interface)

sudo -i (to get a root shell, u can destroy your system in here with the wrong command, be careful, you have root access in here.)

navigate to the directory where the NVIDIA-Linux-x86-177.82-pkg1.run downloaded file is.
if for example you downloaded the file to your Desktop then it would be:
cd ~/Desktop
or
cd /home/yourusername/Desktop

then type:
sh NVIDIA-Linux-x86-177.82-pkg1.run

go through the install, let it compile a kernel module if it needs to, and answer Y when it asks if it can modify your X configuration file(xorg.conf).
(it may tell you you need to install kernel-headers or something else like gcc, binutils, follow the instructions and use 'apt-get install <pkg>' to install what it tells you you need.)

when the install is complete, exit the root shell
type: exit

then restart the graphic interface
sudo /etc/init.d/gdm start

it should work.
-----

before you do this, you obviously have to remove the old driver if you installed it in this manner before and didn't use synaptic or restricted driver ubuntu program.

you would first, after stopping gdm, navigate to where the old driver pkg#.run file is and run the script like usual, but with --uninstall at the end.. like this:
sh NVIDIA-Linux-x86-177.82-pkg1.run --uninstall

uninstall everything to do with nvidia first, this method takes seconds to uninstall and install new drivers. i dont like the built in ubuntu restricted driver thing. from what i see, it's just a kind of frontend to synaptic and getting the current nvidia driver anywayz. and doesn't alwayz work so smooth.
----
after the driver is installed, and /etc/X11/xorg.conf is set up properly, which the driver install should do for you, it doesn't matter what it says about desktop effects, or what it says in restricted drivers program.. you will have full effects.

oh, and also in the beginning make sure to use the restricted drivers program and uninstall anything you installed in there previously, and uninstall all nvidia related stuff from synaptic like i said...(i have this problem where i repeat things..:D:D)

and i dont think it matters, but if run into some trouble, maybe when uninstalling everything, before trying to install new drivers.. run:

lsmod |grep -i nvidia
and if the nvidia module is still loaded, you can run:
modprobe -r nvidia (to remove the nvidia module, then install the new driver, but this is not needed, just throwing it in here in case you need to stop the module manually like that for some reason.)

hope this helps.

u dont need the jockey program(resricted modules)
and u dont need to right mouse click on the desktop and set desktop effects to on or touch it at all for everything to work.

compiz should load up fine now.

---

### Post by risingpowers on 2009-01-12
Thank you for the detailed instructions, cb34. This worked perfecty. :D

---

### Post by cb34 on 2009-01-12
i'm really glad it worked out for you! :D

---

### Post by sofasurfer on 2009-01-12
cb34.
Your solution looks different then what I have tried so far. I will try it out.
But I want to say this first...
I have 5 xorg.conf files. They are 1) xorg.conf 2) xorg.conf.20081231193920 3) xorg.conf.20081231193939 4) xorg.conf.failsafe 5) xorg.conf_backup_2009132325.

Should I have all of these?

---

### Post by cb34 on 2009-01-12
they are backup xorg files that were created by some program/install, x server looks to only xorg.conf for its configuration, unless you specify otherwise.

open your /var/log/Xorg.0.log and check near the top, you should see where it says, using config file: here it should say xorg.conf or whatever config file its using. it will be xorg.conf if you didn't change anything. that's the only file you need to focus on for x server configuration.

---

### Post by sofasurfer on 2009-01-13
sys>admin>hardware-drivers shows nvidia glx 177, 173 and 96 for Ubuntu 8.10. You say to download 177. But the Nvidia site points me to the 180 driver. I can't continue till I get this sorted out. What is the proper driver for the Geforce 7200 card. If it isn't the 180 drivers, then can you post the link to the right one?

---

### Post by sofasurfer on 2009-01-14
I went ahead and attempted with the 180.22 driver (for the 7200 card)which I got from... [http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)

I followed your steps successfully. I cd'd to /home/user/Desktop which is where the driver file is. Then when I got to the "run" command I instead, I typed "NVIDIA-Linux-x86-180.22-pkg1.run" which is exactly the same as the package name. The following error stated "no such file".

Any idea what happened?

EDIT::
I found that I needed to use "sh" as in "sh NVIDIA-Linux-x86-180.22-pkg1.run". Trouble is that I now get the message "can not open package".

---

### Post by cb34 on 2009-01-14
hmmm, are you root when you run the install script?

if you follow my instructions exactly, it will work, or maybe by fluke the file you downloaded is corrupt or something, in that case grab it again.. but i dought it. dont really know man.. sorry.

---

### Post by sofasurfer on 2009-01-14
I found that what I needed to do was to save the Nvidia file to /root/Desktop. Everthing went well. I then exited and on rebooting I ended up with just a black screen. Good thing I have a backup system.

---

