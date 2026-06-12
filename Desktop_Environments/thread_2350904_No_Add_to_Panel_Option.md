---
title: "No Add to Panel Option"
date: 2017-01-28
forum: Desktop Environments
---

### Post by johnnytux2 on 2017-01-28
nm-applet stopped appearing in the upper panel. I've tried a bunch of fixes, but so far nothing has worked. There is however, one fix I have not tried. It requires you to right click the panel and add the notification area. Yet, whenever I right-click the panel, I only have the options Minimize, Maximize, Move, Resize, Always On Top, and Close (with only Always On Top selectable.)  Help is greatly appreciated!

---

### Post by wildmanne39 on 2017-01-28
Please copy and paste the following code into the terminal:
```
sudo apt-get install --reinstall network-manager-gnome
```

---

### Post by johnnytux2 on 2017-01-28
Thanks for the reply! I ran the command, but alas - no change after installing and restarting.

---

### Post by wildmanne39 on 2017-01-28
Please post the results here for the following command:
```
ps aux | grep nm-applet
```
Thanks

---

### Post by johnnytux2 on 2017-01-28
Thanks for the help.  Here is the result: ```
 liltux    3716  0.0  0.0   5148   824 pts/7    S+   21:55   0:00 grep --color=auto nm-applet  
```  nm-applet appears in red, although everything else is white

---

### Post by wildmanne39 on 2017-01-28
It appears to be running, please run this command, I am changing it a little:
```
sudo apt-get install --reinstall network-manager network-manager-gnome
```
What desktop and version of ubuntu are you using?

---

### Post by johnnytux2 on 2017-01-28
I ran the command you supplied, but nothing changed. I am using Ubuntu 16.10 yakkety with the default Unity DE. It may be worth noting that in the login screen after restarting, I am able to see the universal access symbol with the little person and the nm-applet in the panel. but they disappear right after I log in.

---

### Post by wildmanne39 on 2017-01-28
Go into your software center and enable proposed repositories reload the repositories then run update and reboot.

To enable the proposed archive for Ubuntu 16.04 and later use the Software & Updates program and ensure that Pre-released updates (xenial-proposed) is ticked in the Developer Options tab.

---

### Post by johnnytux2 on 2017-01-28
Done. No changes yet :(

---

### Post by wildmanne39 on 2017-01-28
I have researched and have not found a solution so I am moving your post back to desktop environment for better support.

---

### Post by johnnytux2 on 2017-01-28
Thanks for trying!

---

### Post by wildmanne39 on 2017-01-28
Your welcome! most of the time when the nm-applet is missing the command I gave you to run restores it.

You may do a search on while list icon for ubuntu unity and see if white listing them helps.

---

### Post by johnnytux2 on 2017-01-28
I am unable to do anything with the white list. Running commands involving "com.canonical.Unity.Panel" return "No such schema 'com.canonical.Unity.Panel'" and the white list does not exist when I look for it via dconf-editor. I might turn out just starting from scratch, because this is driving me nuts.

---

### Post by deadflowr on 2017-01-28
Try reinstalling the indicator-network package
```
sudo apt-get install --reinstall indicator-network
```
Unity uses indicators in it's panel.

---

### Post by johnnytux2 on 2017-01-29
Thanks for the reply, but no changes yet. I haven't done much to this install, so I'm probably going to (wipe os command - it was deleted for being dangerous) and reinstall later after I finish my work. I just backed up my files and wrote a txt with all the programs and such I had installed - so I'm not too worried about starting over. I'll close the thread if I do reinstall.

---

