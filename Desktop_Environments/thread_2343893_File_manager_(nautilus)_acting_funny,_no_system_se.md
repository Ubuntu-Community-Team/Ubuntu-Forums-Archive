---
title: "File manager (nautilus) acting funny, no system settings on Launcher"
date: 2016-11-20
forum: Desktop Environments
---

### Post by ateator on 2016-11-20
Hey all,
I am running ubuntu16.04
I was trying to install openCV and I ran a script found here: [https://github.com/jayrambhia/Install-OpenCV/tree/master/Ubuntu](https://github.com/jayrambhia/Install-OpenCV/tree/master/Ubuntu)
It ended up doing its thing and finished the install correctly (it seems), but it messed with my system settings such that I had no internet (used apt download network-manager* to download .deb files and reinstalled that way), and my system is acting funny. The settings icon is missing from my launcher and the file manager disappeared. I first tried re-locking a random folder to the launcher and, even though it did lock there, clicking on the icon doesn't open nautilus. I can open nautilus from the terminal. Actually I did unlock the random folder and opened nautilus from the terminal and locked it that way. Its weird, but the right-click menu would still say "Elimination Diet Books" (the random folder) instead of the window I had opened (home).
[ATTACH=CONFIG]272260[/ATTACH]
I have tried:
Reinstalling ubuntu-desktop, gnome-control-center, and unity-control center
apt dist-upgrade
and other random fixes.
This is my terminal after opening nautilus:
[ATTACH=CONFIG]272261[/ATTACH]
Now I have internet and can access system settings using unity-control-center in terminal, but nautilus will not lock to the launcher so that I can click it to open file manager. Sorry if this is a but messy but I'm new to Linux/Ubuntu and I'm still finding my bearings

---

### Post by Frogs Hair on 2016-11-20
The script may have removed some packages when run, try the command below and logout/in or restart  . I'm not at all familiar with openCV.

 ```
sudo apt-get install indicator-session
```

---

### Post by ateator on 2016-11-20
> **Frogs Hair said:**
> The script may have removed some packages when run, try the command below and logout/in or restart  . I'm not at all familiar with openCV.

 ```
sudo apt-get install indicator-session
```

This has worked to get my System Settings icon back, thank you!
Though the file manager is still not working

---

### Post by Frogs Hair on 2016-11-20
Is there a right click/context menu on the desktop ?

---

### Post by ateator on 2016-11-20
Yes there is. If I lock any Nautilus window to the launcher, the right click menu claims that it is in the folder "Elimination Diet Books", no matter what folder I am exploring in

---

### Post by Frogs Hair on 2016-11-20
Let try reinstalling some nautilus packages followed by a restart. ```
sudo apt-get install --reinstall nautilus

``````
sudo apt-get install --reinstall nautilus-data
``````
sudo apt-get install --reinstall libnautilus-extension1a
```

---

### Post by ateator on 2016-11-21
Unfortunately, no, that did not work. Even after the reinstalls, The tooltip that comes up when I mouseover the File Manager in my Launcher still stays "Elimination Diet Books"

---

### Post by ateator on 2016-11-21
When I put a flash drive in, the drive shows up on my Launcher and when I click the icon it navigates to that location in the File Manager correctly. If that helps...

---

### Post by Frogs Hair on 2016-11-21
What does openCV do and is it up to date for the version of Ubuntu you're using ?

---

### Post by ateator on 2016-11-21
openCV (open computer vision) is used for image and video processing. i'm using it with Microsoft Kinect to get the RGBD camera info and use face detecting / skeletal modeling. I am trying to use it with ROS (Robot Operating System), which required that I install openCV2.4.X (an old version). I had that all working, but then I found that script and used it for some forsaken reason and not nautilus is broken.

---

### Post by Frogs Hair on 2016-11-21
If you have synaptic package manager open it up and under the status see if there are autoremovable packages listed , but don't remove them. 

```
sudo apt-get install synaptic
```

The script probably removed some dependencies and packages, so you may have to remove openCV to get things back to normal.

---

