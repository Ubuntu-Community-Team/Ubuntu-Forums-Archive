---
title: "how to install downloaded games?"
date: 2008-12-22
forum: Gaming &amp; Leisure
---

### Post by skathmandoo on 2008-12-22
i just downloaded nexuiz, but i have no idea how to install it. can someone help pls?

---

### Post by frenchn00b on 2008-12-22
> **skathmandoo said:**
> i just downloaded nexuiz, but i have no idea how to install it. can someone help pls?


well, nexuiz is in the repositories
```
apt-cache search nexuiz
nexuiz - A fast-paced 3D Ego-Shooter
nexuiz-data - Nexuiz game data files
nexuiz-music - Nexuiz music files
nexuiz-server - Standalone server for Nexuiz
```

which file did you get?

normally tar xvf file.tar.gz
and then 
./nexuiz
but it depends on the file you have ...

---

### Post by skathmandoo on 2008-12-22
its come up as "nexuiz-242.zip" . i've extracted the file to my documents. i have absolutely no idea wat to do now!!i just switched to ubuntu couple of days ago so i have not even the slightest knowledge about this system.. but hey m getting there. 
thanks for ur help though.

---

### Post by skathmandoo on 2008-12-22
> **frenchn00b said:**
> well, nexuiz is in the repositories
```
apt-cache search nexuiz
nexuiz - A fast-paced 3D Ego-Shooter
nexuiz-data - Nexuiz game data files
nexuiz-music - Nexuiz music files
nexuiz-server - Standalone server for Nexuiz
```
.

this shows up in my terminal as well

---

### Post by eragon100 on 2008-12-22
> **skathmandoo said:**
> its come up as "nexuiz-242.zip" . i've extracted the file to my documents. i have absolutely no idea wat to do now!!i just switched to ubuntu couple of days ago so i have not even the slightest knowledge about this system.. but hey m getting there. 
thanks for ur help though.

You don't have to install it. Open the folder, and double-click on the file called "nexuiz-linux-glx.sh" (or something like that, ends with .sh). Click on "run" in the small dialog that appears. This starts the game. If you want to "uninstall" it, simply remove the folder from your harddrive :wink:

Alternatively, you can install it (with a link in the menu) by simply going to : applications -> add/remove, typing "Nexuiz" in the search box, putting a mark in front of the box, and clicking apply. Then just wait for it to be automatically downloaded and installed, it will say when it's finished :wink:

---

### Post by mikedep333 on 2008-12-23
> **eragon100 said:**
> You don't have to install it. Open the folder, and double-click on the file called "nexuiz-linux-glx.sh" (or something like that, ends with .sh). Click on "run" in the small dialog that appears. This starts the game. If you want to "uninstall" it, simply remove the folder from your harddrive :wink:

Please note that if he merely has the .zip file, he needs to extract it.

You can extract the zip by double-clicking on it so it opens up in file-roller (the archive manager) and then choosing to extract.

Also, in order to run it, you should probably right-click on "nexuiz-linux-glx.sh", go to properties, permissions, and then "allow executing this file as a program" (I think that's what it says.) Then you can right click on it.

---

