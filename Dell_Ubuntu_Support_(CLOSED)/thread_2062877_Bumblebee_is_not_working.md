---
title: "Bumblebee is not working"
date: 2012-09-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 5prasad on 2012-09-25
Hello all,

I am using Dell Xps 15 . I have installed bumblebee for my Nvidia graphic card. Before it was working as the fan is been shut down of graphic card but somehow it's not working and battery is getting consumed alot. 

I am getting this error..


W: Failed to fetch [http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


I tried reinstalling but no use.

Any help appreciated
Thanks in Advance.

---

### Post by katanacb on 2012-10-08
This error looks to me like the software repository information hasn't been setup correctly, or you are having internet connectivity problems.   You might want to check both out...

-Chris

---

### Post by mentorious on 2012-10-12
No, the problem it's completely different. In repository which you use,  are missing packages for Ubuntu 12.04 Precise. 

Look here:
[http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/dists/](http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/dists/)

I found other repository, type:
```
sudo add-apt-repository ppa:bumblebee/stable sudo apt-get update sudo apt-get install bumblebee bumblebee-nvidia
``` Have you installed package "nvidia-graphics-driver" or manually drivers from nvidia.com? If you have already installed drivers from nvidia.com, you must delete them. 

I suggest you add also below repository to system, there are newest graphic drivers ;)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```Then update your system and done :)

----------------------------------------------------
_**Is possible to managment Bumblebee by applet, below have you install instructions:**_
----------------------------------------------------

 1. Install GIT (if you don't have)
```
sudo apt-get install git
```2. Download bumblebee code from git:
```
git clone https://github.com/Bumblebee-Project/bumblebee-ui.git
```3. Go to install :)
```
cd bumblebee-ui
sudo ./INSTALL
```If all will be okay, type this command (location to default installed files after compiling) to launch:
**/usr/local/bin/bumblebee-indicator**

---

