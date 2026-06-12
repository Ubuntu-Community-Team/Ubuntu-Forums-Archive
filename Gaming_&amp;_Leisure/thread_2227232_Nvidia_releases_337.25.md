---
title: "Nvidia releases 337.25"
date: 2014-05-31
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2014-05-31
Wasn't sure whether to put this in the Hardware section or the Multimedia/Video section but I figured due to the gpu driver being so related to gaming performance i'd put it here.

I always run the driver from the Nvidia website ([http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)) , not from the ubuntu repo's, and I wanted to let everyone know that they released version 337.25 which most notably adds support for the following cards
```

GeForce GTX TITAN Z
GeForce GT 740
GeForce 830M
GeForce 840M
GeForce 845M
GeForce GTX 850M
```
But it also patched some bugs (change log is here: [http://www.nvidia.com/Download/driverResults.aspx/76278/en-us](http://www.nvidia.com/Download/driverResults.aspx/76278/en-us) ), I am hoping to get some more FPS out of my GTX 760 with this new driver. 

If you're interested in trying out the driver for your card you must first ensure that you remove all traces of the nvidia driver that you're currently running from the Ubuntu repo's. If your running the nouveau driver than you're ok to proceed with the Nvidia website driver installation. Download the Nvidia driver from the website that you want to use and store it on your desktop. 

**REMOVING UBUNTU REPO'S NVIDIA DRIVER**
Here's a guide for removing the nvidia driver if it was installed from the ubuntu repo's: [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely) 

**DETERMINE WHICH NVIDIA DRIVER YOU'RE CURRENTLY USING**
To find out which driver you're using you can issue the following command
```
lspci -v
```
and look for the line that starts with a number and "VGA compatible controller", if you look within that section you'll see a line that says
> Kernel driver in use: nvidia
This tells me I am running the nvidia driver, NOT nouveau. It's important to note that both the nvidia driver from the repo's and the nvidia driver from their website both state the same thing, "nvidia".

So once you remove all traces of the nvidia driver that you installed from the ubuntu repo's you can now install the nvidia driver from the website. To ensure you're not running the nvidia driver anymore you should restart your machine and see if you have a GUI, if you don't and can't get into your GUI that means you blacklisted the nouveau driver previously and you need to undo whatever you did to make it so that driver wouldn't load. Most times it's a file located within /etc/modprobe.d/ which blacklists the nouveau driver (that's actually what the nvidia website driver does also). Even if you don't have a gui, it's ok cause you're about to install the nvidia driver from the website anyway, so don't fret

**REMOVE PREVIOUS NVIDIA WEBSITE DRIVER**
If by chance you're runnning a previous version of the nvidia driver from the website and you want to upgrade to a newer version, we first have to uninstall the old version before installing the new one. Here's how to do that
If you don't have the .run file you originally used to install that version of the driver, just go download your specific version from the Nvidia website. Once downloaded you would go to a tty session by holding ctrl-alt-f1, that will take you to a text prompt log in screen. Enter your username and password and you should be logged into the virtual terminal console. First we need to stop the running x server by issuing 
```
sudo service lightdm stop
```
then let's make the Nvidia driver install file executable by issuing (this is assuming you downloaded it to your desktop, adjust appropriately)
```
sudo chmod a+x ~/Desktop/NVIDIA-Linux-x86_64-337.25.run
```
now let's run the installer with the uninstall switch
```
sudo ./NVIDIA-Linux-x86_64-337.25.run --uninstall
```
It asks if you want to restore your previous xorg.conf, you can if you want to but i never do. Once the installer is done and you want to install the new version, I always restart my computer with the following command prior to installing the new verison
```
sudo shutdown -r now
```
that shuts down your computer and restarts it, it should boot into a GUI and be running the nouveau driver unless you had previously blacklisted it or uninstalled it.

**INSTALL NVIDIA WEBSITE DRIVER**
Go to a tty session by holding ctrl-alt-f1, that will take you to a text prompt log in screen. Enter your username and password and you should be logged into the virtual terminal console. First we need to stop the running x server by issuing 
```
sudo service lightdm stop
```
so that when you install a new kernel, your graphics driver still works, let's install dkms. (thanks to oldrocker99 for pointing this out)
```
sudo apt-get install dkms
```
then let's make the Nvidia driver install file executable by issuing (this is assuming you downloaded it to your desktop, adjust appropriately)
```
sudo chmod a+x ~/Desktop/NVIDIA-Linux-x86_64-337.25.run
```
now let's run the installer
```
sudo ./NVIDIA-Linux-x86_64-337.25.run
```
I always accept all the defaults, if it says it failed to create the installation package (or something like that) just click ok or yes, you want to continue the install anyway. Once the installer is done than you would issue the following to get back into your desktop window manager
```
sudo service lightdm start
```
and you should be presented with your greeter to login. You're done, you're now running the 337.25 driver. You can look by opening nvidia-settings. Something to note is to always keep the .run installer file, in case you ever want to remove the driver.

It's also worth mentioning that since driver 337.19 they added support for Overclocking your GPU Clock and Memory Transfer. You simply add 
```
Option "Coolbits" "8"
```
and if you want to control your GPU fan you would use 12 instead of 8
to your xorg.conf file under the device section and you'll be presented with boxes for how much you want to OC your card BUT I will say that I haven't figured out how to apply the OC values. It does appear that the Preferred Mode drop down does work though, when I select Prefer Maximum Performance the Graphics Clock goes up to 135MHz and 1293MHz and the Memory Transfer Rate goes up to 6008MHz
[IMG]https://lh6.googleusercontent.com/-EuNzrLUHdSI/U4n1iGzEiHI/AAAAAAAACug/8SKnY7ryiLY/s800/nvidia-settings.png[/IMG]

---

### Post by oldrocker99 on 2014-05-31
Very comprehensive guide, with all pertinent info included. Nice job!

---

### Post by MikeCyber on 2014-06-01
I've never used the uninstall. When installing as above the latest, the installer tells you that it will uninstall the old driver.-

---

### Post by adec2 on 2014-06-01
Personally i find it easier using the xorg edgers ppa but thanks for this anyway

---

### Post by oldrocker99 on 2014-06-02
One thing I missed, though. Before you install any driver downloaded from nVidia, do this first:
```
sudo apt-get install dkms
```

You'll be glad you did when there is a kernel update; otherwise, you'll have no graphic driver when the kernel updates.

---

### Post by dannyboy79 on 2014-06-04
> **oldrocker99 said:**
> One thing I missed, though. Before you install any driver downloaded from nVidia, do this first:
```
sudo apt-get install dkms
```

You'll be glad you did when there is a kernel update; otherwise, you'll have no graphic driver when the kernel updates.

updated post, thanks

---

### Post by oldrocker99 on 2014-06-04
You're most welcome!

---

### Post by szandor420 on 2014-07-07
well damn. cpu temps went from 50c to 40c with mbp 10,1 runnng kali and no power tweaks.

---

### Post by oldrocker99 on 2014-07-08
I've been running 3.40.17 lately, BTW.

---

### Post by dannyboy79 on 2014-07-08
i see 340.24 here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) but no 340.17??

---

### Post by oldrocker99 on 2014-07-09
Apparently, there's been an update since I installed 3.40, which is the only problem with installing nVidia drivers manually. You do have to check to see what's new on your own, unlike using the repos.

---

