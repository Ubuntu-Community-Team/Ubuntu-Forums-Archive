---
title: "Ubuntu On Dell Latitude XT"
date: 2008-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Langrood on 2008-05-13
Hi Folks

I just want to mention some of the difficulties one may experience during and after the installation of Ubuntu on Dell XT and the answers to get around those problems.

When you start installing Ubuntu, most probably the first thing you face is the lack of Xserver. What you should do then is to  get connected to a wired internet connection and install the new "fglrx" driver. Do the Following:

1) open one terminal(tty) by Cntl+Alt+F1
2) sudo aptitude install xorg-driver-fglrx
3) sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.old
4) sudo nano  /etc/X11/xorg.conf
5) find the Device "VESA" and change it to "fglrx"
6) Cntl+X, Y, Enter
7)sudo /etc/init.d/gdm restart

another problem you might face after installation is that wireless does not work. To solve the problem follow the instructions stated in the following URL:
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

You may also experience sound problem which will easily be tackled by :
sudo apt-get install linux-backports-modules-generic & reboot 

Good Luck

---

### Post by tomyhayes on 2008-08-23
[QUOTE=Langrood;4952538]Hi Folks

1) open one terminal(tty) by Cntl+Alt+F1
2) sudo aptitude install xorg-driver-fglrx
3) sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.old
4) sudo nano  /etc/X11/xorg.conf
5) find the Device "VESA" and change it to "fglrx"
6) Cntl+X, Y, Enter
7)sudo /etc/init.d/gdm restart


After Doing this computer freeze with a black screen.. (I add the line "Driver   "fglrx"" in Device). any help? I'm stuck with windows..:(

---

### Post by Langrood on 2008-10-08
Hey, 
I have no idea. but I took the same steps with Ubuntu 7.10 and I have been running Ubuntu on XT without any difficulty.

---

