---
title: "Nvidia Drivers?"
date: 2006-03-12
forum: Desktop Environments
---

### Post by NeghVar on 2006-03-12
I have a GeForce MX4000 and Ubuntu 5.10. What drivers do I need and how would I go about getting them?

---

### Post by hw-tph on 2006-03-12
Install the nvidia-glx package: **sudo apt-get install nvidia-glx**
If your card is old and not supported by current nvidia drivers you need to installed the nvidia-glx-legacy package instead of nvidia-glx.

Then, if you haven't edited your xorg.conf by hand simply do this to enable the nvidia driver in place of the X.org nv driver: **sudo nvidia-glx-config enable**

That should be it!


Håk

---

### Post by Sutekh on 2006-03-12
[QUOTE=NeghVar]I have a GeForce MX4000 and Ubuntu 5.10. What drivers do I need and how would I go about getting them?[/QUOTE]
Try this thread

[Ubuntu Forums - HOWTO: Latest NVIDIA Drivers]("http://ubuntuforums.org/showthread.php?t=75074")

Method 1 (dead easy)  - install NVIDIA drivers from Ubuntu repository

Method 2 (slight harder) - install official NVIDIA drivers

---

### Post by NeghVar on 2006-03-12
thanks guys, I seem to have gotten it goin here. i wasnt sure which packages i needed.

---

### Post by haddog on 2006-03-12
[QUOTE=hw-tph]Install the nvidia-glx package: **sudo apt-get install nvidia-glx**
If your card is old and not supported by current nvidia drivers you need to installed the nvidia-glx-legacy package instead of nvidia-glx.

Then, if you haven't edited your xorg.conf by hand simply do this to enable the nvidia driver in place of the X.org nv driver: **sudo nvidia-glx-config enable**

That should be it!


Håk[/QUOTE]
hw-tph, your method worked perfectly. I am running Dapper Drake Flight 5. After installation of Flight 5, I installed all the system updates. Rebooted and the installled the nvidia-glx package with apt-get. Restarted the computer and got the Nvidia splash screen.

---

### Post by terranz on 2006-03-12
I have the same video card and have installed drivers in mandrake and suse.  I looks like installing them in unbuntu is going to be easier :-k

---

### Post by High Plains Drifter on 2006-03-16
[QUOTE=terranz]I looks like installing them in unbuntu is going to be easier :-k[/QUOTE]

like most things are.

---

### Post by terranz on 2006-03-16
it was but I lost access to some resolutions

---

### Post by Sutekh on 2006-03-16
[QUOTE=terranz]it was but I lost access to some resolutions[/QUOTE]
You can get them back if you wish.

Re-configure the X server
```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked a string of questions, that you can answer as suggested by the program, or change if you require.  If there is something you are not sure about then go with the suggested/default.  I pretty much press Enter the entire time.  

Eventually you will get to a screen that will allow you to choose the resolutions for X.  Just enable the ones that you want.

---

### Post by terranz on 2006-03-16
Thanks for the commands.  I assume from your description that it's like running xf86config?

Running that always messed up my mouse options but ubuntu seems to do things well so I'll be optimistic with this.

---

### Post by Sutekh on 2006-03-16
Yeah I imagine that they are similar.  There are questions relating to your input devices; keyboard, mouse and video, so I guess be careful with those regarding your mouse.

Also I should have said to make a backup of the xorg.conf file first
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
before running the dpkg-reconfigure.  If things go awry you can restore your old settings (which do work)

---

### Post by terranz on 2006-03-16
Thanks I'll give it a try

---

### Post by terranz on 2006-03-16
works :D 

I'm now in a higher resolution.  Now I can see why people are complaining about the new forum layout.

---

### Post by ctucker10 on 2006-05-30
hw-tph

Thanks for the quick and easy instructions for getting my new video card working. Ubuntu is most definately the best Linux distro I've tried...I've tried several.

---

