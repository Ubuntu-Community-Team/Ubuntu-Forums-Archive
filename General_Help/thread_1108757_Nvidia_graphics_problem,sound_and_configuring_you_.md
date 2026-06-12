---
title: "Nvidia graphics problem,sound and configuring you monitor"
date: 2009-03-28
forum: General Help
---

### Post by Dileeshvar on 2009-03-28
Hello friends here is how I solved my resolution ,
sound and monitor problem.
I use ASUS P5N-MX mother board ,GeForce 750GPU graphic card,
and AOC 17" monitor.

AUDIO:

First, with the fresh install of download ubuntu 8.04, the audio did not work. I made all the updates of ubuntu over internet and after I did the code proposed by Temüjin :
```
sudo update-pciids
```

GRAPHICS

After that, I had a problem to set the native resolution.When I tried to install the restricted driver with the graphical utility in System/Administration/Restricted Drivers Manager the display manager did not work. So here's how to make nVidia drivers work :

First uninstall the nVidia drivers provided by the Restricted Drivers Manager.

After go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). Select Linux IA32 latest version if you have 32bits distribution or AMD64 if you have ubuntu AMD64. Download and save it on your desktop.

Go where you saved the file and right click on it, select propreties. Go into permissions and mark the box "Allow executing file as a program".

Now you have to close your display manager. Close all you programs, log out and press ctrl+alt+F1. You will enter in a console that is not on the display manager. Log with your normal user and password.

First close your display manager. Type :
```
killall gdm
```

replace gdm by kdm for KDE display manager.

Go to the directory where you saved the nVidia driver for linux. Type
```
cd Desktop
```

and then

```
sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg1.run
```

verify the version that is written. If the version is different, change it on the command above. To see the files you have in the directory you are, type "dir".

Now follow the step by step installer. At the end it is asked if you want to configure your xorg.conf. Say yes, this will select the nvidia driver. Now nVidia driver is installed!

When you return to the console type:
```
sudo gdm
```

You should see the nVidia logo before the login screen.

Enjoy!

still if it asks for any libraries generally its this 

try installing this
```
sudo apt-get install libc6-dev linux-libc-dev linux-headers-generic
```


This shoul do generally with normally any monitors

but mine did not respond still
 so if your resolution is still not set
its problem with your monitor
just google about your monitor and find out horizontal synchronization and vertical refresh module present this is generally enough

then go to 

```
vim /etc/X11/xorg.conf
```

change the required and restart your system.

It works :)
:guitar:

---

### Post by DeMus on 2009-03-28
> **Dileeshvar said:**
> To see the files you have in the directory you are, type "dir".

You must be a former Windows user. To list files in a folder you have to type ls, or with more information about those files ls -l.

---

### Post by Dileeshvar on 2009-03-28
I was by the way but not now !!
but I do know those ls commands y do u want to highlight it here ??

---

