---
title: "Accidentally uninstalled Gnome Network Manager"
date: 2009-05-12
forum: General Help
---

### Post by Texan29 on 2009-05-12
Well I messed up! :(  I'm just getting back into Linux after being gone for about 10 years... so consider me a major beginner 

I was trying to get VPN enabled in Gnome Network Manager and found someone had success typing "sudo apt-get -y install network-manager-pptp" in the terminal to get VPN enabled, I didn't realize until too late that this was going to uninstall Gnome Network Manager and install this pptp which I don't even know how to use....

Bottom line is I need Gnome Network Manager back, but I can't install it through synaptics because I don't have any network connections anymore.  I don't know what debs I need to install to get it back online for my system version, can anyone point me in the right direction and tell me how to get Gnome Network Manager back.

Links to files and step by step instructions would be much appreciated.

System Info:  Dell Mini 12, Ubuntu 8.04 dell version

---

### Post by kpkeerthi on 2009-05-12
[http://packages.ubuntu.com/jaunty/network-manager-gnome]("http://packages.ubuntu.com/jaunty/network-manager-gnome"). Scroll to the bottom of the page and you will find the Download section. Click on the CPU architecture that applies to you.

Copy the deb file to you home folder and run
```
sudo dpkg -i *.deb
```

If it complains about missing dependency, download the dependencies listed on the [page]("http://packages.ubuntu.com/jaunty/network-manager-gnome") and run **sudo dpkg -i *.deb **again. Repeat this step until all dependencies are resolved.

Or download the alternate CD ISO. Add it as a repository and install the package network-manager-gnome using synaptic.

---

### Post by Texan29 on 2009-05-13
I was able to get it reinstalled last night, thank you for your help!

---

