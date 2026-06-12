---
title: "desktop doesn't show after install over server"
date: 2008-04-11
forum: Desktop Environments
---

### Post by Terminating.proprietary on 2008-04-11
OK, here is the issue. I installed a server install on my friends machine because I could not get the desktop live cd to boot up. So I figured I would install the desktop over top so i eventually did
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
```how to install desktop over server
I don't even know what gdm is I am guessing gnome?
When I boot it just boots to the command line interface.
I am thinking maybe I need to install another package or I need to change a configuration file to boot to desktop or perhaps I need drivers for the desktop but i would assume they had installed with it and if I didn't have drivers I would get some kind of message on boot, rather it just boots to the command line. Please help thanks.

---

### Post by warp99 on 2008-04-11
You can start the desktop if you login and type 'startx', but I believe you want a login screen as well. You also need to install a desktop kernel since this kernel includes some modules that the server kernel does not. So do the following:

```
sudo apt-get install linux-image-2.6.22-14-generic
```

after that reboot to load the new image, login to the command prompt, then:

```
sudo apt-get remove --purge gdm && sudo apt-get install gdm
```

reboot, then you should have a login screen.

Edit:
Your using Gusty 7.10, correct? You may have to reconfigure xserver. So run 'sudo dpkg-reconfigure xserver-xorg' after you install gdm.

---

### Post by Terminating.proprietary on 2008-04-11
Yea gutsy 7.10 I am pretty sure I am going tp try this now

---

### Post by warp99 on 2008-04-11
One more thing, if gdm still doesn't show then try:

```
sudo dpkg-reconfigure gdm
```

---

### Post by Terminating.proprietary on 2008-04-11
Ok, thanks, I'll let you know I am rebooting now.

---

### Post by Terminating.proprietary on 2008-04-11
ok i reconfigured gdm and now am rebooting hopefully that will work sudo startx returns a fatal error

---

### Post by Terminating.proprietary on 2008-04-11
Also, instaling the other kernal added the generic option to my boot menu, should I be doing this reconfiguring etc on that because I did it on the server....

---

### Post by warp99 on 2008-04-11
Yes base it on the new kernel. Also there is no 'sudo' startx, just startx after you login.

---

### Post by Terminating.proprietary on 2008-04-11
OK, well startx doesn't work either and I have done everything and no dice only thing I get is I see starting gnome display manger when I start up and stopping if I shut down yet i never actually see the desktop lol

---

### Post by warp99 on 2008-04-11
Did you reconfigure the xserver?

---

### Post by Terminating.proprietary on 2008-04-11
Yes, maybe I did it improperly but I basically just stuck with the defaults or what it detected

---

### Post by Terminating.proprietary on 2008-04-11
startx outputs some jumbo then
```
Fatal server error;
No valid FontPath could be found.
X10: fatal IO error 104 (connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed0 with 0 events remaining.
xauth:  error in locking authorityu file home/chad/.Xauthority
```

---

### Post by warp99 on 2008-04-11
From what you telling me the login manager is starting, but the display is not working. So when you run 'sudo dpkg-reconfigure xserver-xorg' choose the 'vesa' driver for the display and a monitor resolution of 1024x768 or 800x600. 

No need to use the 'startx' command since you're at the point of a login screen, just no display.

---

### Post by Terminating.proprietary on 2008-04-11
> **warp99 said:**
> From what you telling me the login manager is starting, but the display is not working. So when you run 'sudo dpkg-reconfigure xserver-xorg' choose the 'vesa' driver for the display and a monitor resolution of 1024x768 or 800x600. 

No need to use the 'startx' command since you're at the point of a login screen, just no display.

I am still at the command prompt

---

### Post by Terminating.proprietary on 2008-04-11
ok I see what you mean I am reconfiguring now

---

### Post by Terminating.proprietary on 2008-04-11
I reconfigured and I still have just the command line interface

---

### Post by warp99 on 2008-04-11
Try this command:

```
sudo apt-cache policy ubuntu-desktop
```

Does it show ubuntu-desktop as installed?

---

### Post by Terminating.proprietary on 2008-04-11
LOL, no I am installing it now I didn't realize that when I installed the generic i would have to reinstall everything. But then again on the server install I am pretty sure that had also said gdm was running and the desktop was installed, yet no desktop.

---

### Post by warp99 on 2008-04-11
No you don't have to reinstall the desktop when you switch kernels, it just didn't get installed completely the first time. So make sure ubuntu-desktop is installed, it should install about 100 or more packages, and if the login manager does not start try this command:

```
sudo /etc/init.d/gdm start
```

---

### Post by Terminating.proprietary on 2008-04-11
Ok can I get rid of the server kernal and how because i am out of disk space and can not install the entire desktop...

---

### Post by warp99 on 2008-04-11
If your out of space you're in trouble because the server kernel is only about 50MB of data. You may have to expand the partition in order to have space to retrieve all of the packages.

---

### Post by Terminating.proprietary on 2008-04-11
Anyway to install the desktop without all the stuff life open office? to save space

---

### Post by Terminating.proprietary on 2008-04-11
> **warp99 said:**
> If your out of space you're in trouble because the server kernel is only about 50MB of data. You may have to expand the partition in order to have space to retrieve all of the packages.

Well I think it is just too much cached and I didn't get enough space to root. The whole hd is 7.5GB and is dual booting with windows XP so yea 50mb could make or break the install

---

### Post by warp99 on 2008-04-11
How is the partition table on the drive setup? You can expand it very easy using gparted on the install disc or download the gparted LiveCD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Once you do that you can install the desktop rather easy with plenty of space. If you can't do that the best thing is a re-install and make the partition larger during setup since you're bumping up against a drive space issue that going to crop up in the future because right now the packages you're installing are about 200-300 MB plus the archives for a total of about 400-500MB. Not a lot of wiggle room for the future.

Edit:

BTW how big is the Ubuntu partition?

---

### Post by Terminating.proprietary on 2008-04-11
Well i though ubuntu was small, is there a way to install without all the junk. The partition is 2 GB I can't spare more.

---

### Post by warp99 on 2008-04-11
You can install Xubuntu which has the XFCE desktop instead of Gnome. It's smaller, doesn't include Open Office, and will fit on your partition with a full desktop. You would install it like this:

First clear out all of the downloaded archives with Ubuntu:
```
sudo apt-get clean autoclean
```
and uninstall gdm and the server kernel
```
sudo apt-get remove --purge gdm linux-image-2.6.22-14-server 
```
that should be the correct server kernel if not change it to the server kernel that's installed on your system, then install the Xubuntu desktop:
```
sudo apt-get install xubuntu-desktop
```
reconfigure xserver:
```
sudo dpkg-reconfigure xserver
```
then finally:
```
sudo apt-get clean autoclean
```
to clean out the downloaded archive. Once you get this installed you can clean out some of the server applications such as apache and mysql if you need more space.

Xubuntu may be a better option if your system is older with limited amount of ram and disk space. Check it out here:

[http://xubuntu.org/](http://xubuntu.org/)

---

