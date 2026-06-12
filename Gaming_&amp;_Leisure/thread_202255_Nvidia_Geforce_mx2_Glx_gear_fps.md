---
title: "Nvidia Geforce mx2 Glx gear fps"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by CameronCalver on 2006-06-23
Hello i have a old nvidia geforce mx 2 2 and i run glxgears -printfps and i get this  
cameron@ubuntu:~$ glxgears -printfps
231 frames in 5.1 seconds = 45.337 FPS
2224 frames in 5.1 seconds = 438.459 FPS
3525 frames in 5.1 seconds = 694.402 FPS
1819 frames in 5.0 seconds = 363.198 FPS
1692 frames in 5.0 seconds = 336.225 FPS
1947 frames in 5.1 seconds = 385.152 FPS
1391 frames in 5.0 seconds = 275.846 FPS
1303 frames in 5.1 seconds = 255.128 FPS
1763 frames in 5.0 seconds = 349.590 FPS
1840 frames in 5.1 seconds = 363.192 FPS
1362 frames in 5.1 seconds = 266.659 FPS
1718 frames in 5.0 seconds = 343.036 FPS
1816 frames in 5.0 seconds = 361.420 FPS
1495 frames in 5.0 seconds = 296.161 FPS
1721 frames in 5.1 seconds = 338.135 FPS
2149 frames in 5.0 seconds = 427.483 FPS
1736 frames in 5.1 seconds = 343.227 FPS
929 frames in 5.0 seconds = 183.972 FPS
3039 frames in 5.0 seconds = 603.768 FPS


i know that geforce 2 are old but people are getting like 1500 fps and i would expect that thwe nvidia geoforce mx2 would perform better then that can i check if i have the drivers installed

---

### Post by SquatcHman on 2006-06-23
Check your xorg.conf file to make sure that X is configured to use "nvidia" instead of some other driver.  

You could also run "glxinfo | grep direct" from the terminal to see if direct rendering is enabled.  

If you aren't certain that the driver is installed or not then it probably isn't installed.  I know that I use automatix to install it for me.  [http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by CameronCalver on 2006-06-23
yes it is all installed i found out that a program was doing a backup in another workspace and it was slwoing it down lol i feel stupid

---

