---
title: "Can't Shut Down X server in 12.04"
date: 2012-05-04
forum: Desktop Environments
---

### Post by SevenThunders on 2012-05-04
This is really bizarre but I need to run the nvidia proprietary drivers for the latest CUDA support. As many have noted the proprietary Nvidia drivers (295.40) are very buggy causing 3D acceleration to fail.
(see)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485)

So some new drivers were released and I wanted to install them, but no method I have tried allows me to actually shut down the X server so that I can run the driver install.

I can log into the recovery console, but X is still running.  OK fine I then run sudo /etc/init.d/gdm stop.

Sorry X is still running.  OK I will kill the X process then after finding the process ID via ps axl.
(eg sudo kill -9 xpid)

Nope that kills the whole console session and restarts X.  Same thing happens with  rightAlt-print-k  .  telinit 3 gives me the same useless loop.  X will just automatically restart.

I'd say this is pretty useless behavior.  Whats the preferred way of killing X to install proprietary video drivers?  I've spent about an hour trying to find it.

---

### Post by SevenThunders on 2012-05-04
Apparently running console recovery from the main grub menu is utterly useless as well.  It starts in freakin read only mode!  So no changes can be made!  How useful.

I can't believe this.  There is no way to turn off X and run a basic console that is of any use?  It's insane!

Supposedly from the grub menu there is a way to force runlevel 2 or 3.  That's my only hope now.

---

### Post by mips on 2012-05-04
Boot your system and login followed by Ctrl-Alt-F1 and execute **sudo /etc/init.d/lightdm stop**

I don't think ubuntu uses gdm anymore, it's lightdm now. Anyway, the above worked for me when I had to install the nvidia drivers

---

### Post by lolpenguin on 2012-05-04
> **mips said:**
> Boot your system and login followed by Ctrl-Alt-F1 and execute **sudo /etc/init.d/lightdm stop**

I don't think ubuntu uses gdm anymore, it's lightdm now. Anyway, the above worked for me when I had to install the nvidia drivers

```
sudo service lightdm stop
``` I find it annoying to type /etc/init.d/lightdm.

---

### Post by mips on 2012-05-04
> **lolpenguin said:**
> ```
sudo service lightdm stop
``` I find it annoying to type /etc/init.d/lightdm.

I don't type, I copy & paste :lolflag:

---

### Post by SevenThunders on 2012-05-04
> **mips said:**
> Boot your system and login followed by Ctrl-Alt-F1 and execute **sudo /etc/init.d/lightdm stop**

I don't think ubuntu uses gdm anymore, it's lightdm now. Anyway, the above worked for me when I had to install the nvidia drivers

Yeah thanks for posting this.  I did finally figure it out.  I forgot the service I needed to stop was lightdm not gdm.  Still it seems odd that we can't easily log into a text only console from any of the login windows.  

IMHO recovery mode login should not have X windows running.

---

### Post by markbl on 2012-05-05
The proper way to stop this in ubuntu 12.04 is:

sudo service lightdm stop

---

### Post by Palletje on 2012-07-03
sudo service lightdm stop
sudo lightdm stop
sudo /etc/init.d/lightdm stop
 
all of the above commands are not working for me, I am sure i am running ubuntu 12.04
 
So when i run the newest driver, downloaded from the nvidia site, it still gives me the error that x-server is still running
 
I tried to find the pid and stop that manually and that seem to have worked for me. installed it, rebooted the machine, hower when i start the graphics version of the nvidia x-server setting it says that I am not using a nvidia x-server driver?
 
Anyone that know how to fix this?

---

### Post by MausTee on 2012-07-27
[FONT=Arial]@seventhunders, 
I ran into the same problems. To install the Nvidia drivers you have to gain root acces. In the terminal type '**sudo su -**' (enter), then followed by your password. 
After this you can install the driver with the next commands:
[/FONT] [FONT=Arial]**sudo apt-get install nvidia-current** 
(or nvidia-173 or nvidia-96, depending on your card)
[/FONT][FONT=Arial]**sudo nvidia-xconfig** [/FONT][FONT=Arial](Configure your xorg.conf)
    [/FONT][FONT=Arial](Restart your computer)

See also: [/FONT] [FONT=Arial][http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu](http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu) 

I hope it works for you! [/FONT] [FONT=Arial]:P[/FONT]

---

### Post by efflandt on 2012-07-27
The best way to get newest drivers and have them compatible with Ubuntu is to add the x-swat repository:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

Then installing **nvidia-current** (with sudo apt-get or Synaptic) should get you most recent nvidia drivers after reboot.

If you currently have mixed drivers from package install and manually installed from nvidia website, good luck.  Not sure how you would straighten that out.  I had enough problems trying to resolve bits and pieces of current version and post-release updates packages from using both gui and apt-get in console in 11.10 when trying to fix a failing video card, that I had to reinstall Ubuntu.

I have not had any trouble with my GTX 550 Ti in 64-bit 12.04 other than having to use nomodeset for live/install iso (no kernel parameters needed after install with regular nvidia-current).

---

### Post by HousieMousie2 on 2012-08-15
> **markbl said:**
> The proper way to stop this in ubuntu 12.04 is:

sudo service lightdm stop

Thank you!  No more fighting with init run levels!

*SevenThunders: The read-only mount state in recovery is horrid... really don't see much use for it.

---

### Post by robert365 on 2012-08-16
Do the drivers that come from here have the same functionality as the proprietary drivers from NVIDIA? 

Also, I'm wondering if it is possible to install the proprietary drivers in a package like fashion? Or is that the whole point of this repository: that it offers the proprietary drivers in a package format.

Or is it even necessary to have it in a package format? For example, is it trivial to uninstall the proprietary driver at a later point in time.

Last question I promise: how does the repository give me the correct driver for my device? Or is it just a cover-all generic driver that works for most NVIDIA devices?

Many thanks

---

