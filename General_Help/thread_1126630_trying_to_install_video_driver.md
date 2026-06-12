---
title: "trying to install video driver"
date: 2009-04-15
forum: General Help
---

### Post by hurstdaj on 2009-04-15
I'm still working on getting my display settings working correctly.  I'm going to try installing the package downloaded from nvidia.  The only problem is that I have no idea how to run the package. I get the following error:

```
ERROR: nvidia-installer must be run as root
```

How do I run this file as root?

---

### Post by hikaricore on 2009-04-15
```
sudo ./filename
```

---

### Post by hurstdaj on 2009-04-15
I am completely new to Ubuntu.  Where do you enter this command?  

If the filename is ```
NVIDIA-Linux-x86-180.44-pkg1.run
``` saved to desktop, would the correct code be ```
sudo ./NVIDIA-Linux-x86-180.44-pkg1.run
```

---

### Post by hurstdaj on 2009-04-15
Is there anyone who can help me with the command to launch the video package from root?

---

### Post by jwheel12 on 2009-04-16
sudo sh NVIDIA-Linux-x86-180.44-pkg1.run

I've been trying to get this package to install correctly for 3 hours. I get the no screens found error every time.

I have been unable to install ANY nvidia display drivers without getting the same error.

GOOD LUCK

---

### Post by bollix47 on 2009-04-16
When installing NVIDIA drivers I do the following:

1.  ctrl-alt-F1 after closing all open programs ...  this will bring you to a login prompt
2. login using your login name and password
3. sudo /etc/init.d/gdm stop
4. sudo apt-get purge nvidia-*
5. using the cd command change to the folder containing the NVIDIA*.run file  (e.g. cd Desktop)
6. sudo sh NVIDIA-Linux-x86-180.44-pkg1.run (numbers may be different depending on version)
   I pretty much just press enter for the defaults(might have to press tab to get to the OK for accepting license) and make sure to choose yes when asked to update xorg.conf
7. sudo reboot

You should see the NVIDIA splash screen as Ubuntu boots up

Good Luck

---

### Post by hurstdaj on 2009-04-16
It appears that I'm on the right track, and I do appreciate the spelled out instructions.  It does wonders for a Linux dummy like me.  I made a couple of attempts, but think that I've finally found the correct driver.  It gives an error message that I'm running an X-server and to exit it before installing.  How do I exit the X-server, and what is it?  :oops:

---

### Post by CatKiller on 2009-04-16
> **hurstdaj said:**
>  How do I exit the X-server?

3. sudo /etc/init.d/gdm stop

You should be able to install NVidia's driver with the System -> Administration -> Hardware Drivers tool.

I understand you've been having resolution problems.

Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

---

### Post by Xiangxianni on 2009-04-16
Since you are not familiar with command line and shell,
I think you can install it by other GUID software,such as EnvyNG.

---

