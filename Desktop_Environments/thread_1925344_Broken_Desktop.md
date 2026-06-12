---
title: "Broken Desktop"
date: 2012-02-14
forum: Desktop Environments
---

### Post by nick0 on 2012-02-14
Hello everyone.

I have been using ubuntu 64bit for the last few months. Unity sucks. I'm using gnome. But after a reboot I have been unable to get them working. It shows me a unity login screen. When I chose gnome or unity it starts... gives me my background... and transmission that starts on boot. From transmission I can get into firefox. 

I'm assuming its an update that broke everything. If anyone needs me to run a command I will gladly give you the output. Thanks in advance.

---

### Post by Yarolinux on 2012-02-14
Did you recently 'remove obsolete packages' ?

---

### Post by jerrrys on 2012-02-14
sudo apt-get update

---

### Post by jerrrys on 2012-02-14
> **Yarolinux said:**
> Did you recently 'remove obsolete packages' ?

A good way to remove obsolete packages it with synaptic package manager.

[http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html](http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by nick0 on 2012-02-14
i tried this already...
sudo apt-get update
sudo apt-get upgrade

i also thought it might be something with grub starting the wrong kernel  or something... (i triple boot Ubuntu, Windows, Backtrack)
update-grub

and that didnt fix it. its probably broken packages... i did not remove obsolete packages. i tried to install synaptic many times but failed. i will try and install it later... does anyone have a way of doing that from terminal? is it "sudo apt-get autoremove"?

---

### Post by jerrrys on 2012-02-15
sudo apt-get clean

sudo dpkg --configure -a

sudo apt-get install -f

Are you getting any error messages?

---

