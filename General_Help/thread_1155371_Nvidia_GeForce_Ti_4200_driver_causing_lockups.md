---
title: "Nvidia GeForce Ti 4200 driver causing lockups"
date: 2009-05-10
forum: General Help
---

### Post by Wyldfire on 2009-05-10
Have checked forums, but still haven't found adequate answer.

Ubuntu 9.04

Latest possible nVidia drivers ([nvidia-graphics-drivers-96 - 96.43.10-0ubuntu2       ]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/581463/+listing-archive-extra"))

Enabling the drivers causes system to freeze constantly (1-2 times a minute)

Without the drivers, most of my multimedia content (mythtv, etc...) runs badly, if at all.

Is there any way to stop the drivers from killing my system?

Much thanks,

Leif

---

### Post by fooman on 2009-05-10
are the visual effects enabled?  ...if so,  turning them off should help (i think they are usually enabled by default).

system > preferences > appearance > visual effects tab....try setting to "none"

---

### Post by Wyldfire on 2009-05-10
Already set to none, though the machine should be able to handle it even if they were enabled.  I found some references that it may be a conflict between the driver and the cpu clock, but I haven't found any way to fix the problem.

Are there any diagnostics I should run?  Any other info that would be helpful?

---

### Post by Wyldfire on 2009-05-10
Bump... has anyone got any ideas?

---

### Post by Crafty Kisses on 2009-05-10
Have you tried downloading and installing the drivers via the official nVidia website? I'm just guessing you have 32-bit, but I'll provide both 32 and 64-bit links. 

32-bit: [http://www.nvidia.com/object/linux_display_x86_96.43.11.html](http://www.nvidia.com/object/linux_display_x86_96.43.11.html)
64-bit: [http://www.nvidia.com/object/linux_display_amd64_96.43.11.html](http://www.nvidia.com/object/linux_display_amd64_96.43.11.html)

Once you have downloaded the nVidia driver you need to stop your X server, so press Cntrl+Alt+F2. Once you have done that you need to run the following:
```
sudo /etc/init.d/gdm stop
```
Then once you've done that you need to run the following, remember I'm just guessing the file is called NVIDIA-Linux and it's saved to your desktop, so remember substitute your information:
```
cd ~/Desktop
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run
```
Once the installation is done, restart the X server with:
```
sudo /etc/init.d/gdm start
```
If you have any problems with this driver, you can remove it by running the following:
```
sudo sh NVIDIA* --uninstall
```
Where the * is, you need to put the correct driver information. Remember to backup your X just in case anything happens, you can do this by running the following:
```
sudo cp /etc/X11/xorg.conf ./xorg.conf.backup
```
You also may need "build-essential" installed, you can install it by running the following command:
```
sudo apt-get install build-essential
```
Remember to remove your old nVidia drivers first.

---

### Post by fooman on 2009-05-11
ti-4200 is a really old card (i know,  i have one of those lying around somewhere)....maybe try an older driver.

i believe there is a 71.86.08 available in the repos....maybe try that and see if its any better.

good luck.

---

### Post by Wyldfire on 2009-05-19
Guess I'll try to save up for a new card... no luck with the driver on this one.

---

