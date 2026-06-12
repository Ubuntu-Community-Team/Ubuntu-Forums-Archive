---
title: "apt-get install......."
date: 2008-12-31
forum: Desktop Environments
---

### Post by visitnag on 2008-12-31
I am more familiar with rpm packages and recently started using Ubuntu(just beginner). 

1)Kindly explain me what happens when we use apt-get install <package name> is opted? 

2)Can i see the package download? 

3)Can i install the same package after downloading from the net? 

4)I am starting internet connection by using sudo pon command. Cont i get any graphical icon on the desktop (like in windows) to start and disconnect the broad band connection? (as we are having a download limit)

5)why to use sudo command before every bash command?

(i dont have problems using command prompt commands,)

---

### Post by SuperSonic4 on 2008-12-31
1. You fetch the package from a repo (like yum and urmpi do with rpm) and when it's done it installs them.

2. ```
sudo apt-get -s install <package>
``` will do a test run (-s is simulation)

3. It downloads from the net, You can't have the same version of the same program as far as I know but you might

4. KNetworkManager does the job for me in Kubuntu, I think network-manager is the ubuntu equivalent

5. You don't for most, just when you need root. You don't need sudo to *cd* for example or to run things as user. Essentially you need sudo to alter system files and installing downloads to /usr which is a root file. sudo pon looks like it edits /etc/hosts - another system file

---

### Post by BoneSaw on 2008-12-31
1) apt-get install <package name> queries the repositories for the package, then downloads and installs it.

2) you can watch it download, however it goes very fast. if you watch the terminal it will say "fetching" i believe and be represented as a 0%.

3) if you find a deb package online and wish to install it you can do so by using the command  sudo dpkg -i <package>

5) the sudo is only used on commands that need root privelege. it shouldnt be used on *every* command as it can cause biiiiig problems.

---

### Post by 2hot6ft2 on 2008-12-31
> **visitnag said:**
> 
4)I am starting internet connection by using sudo pon command. Cont i get any graphical icon on the desktop (like in windows) to start and disconnect the broad band connection? (as we are having a download limit)

Network Manager is in the top right on the taskbar, you can right click on it an enable/un-enable networks.

---

