---
title: "Installing kubuntu-desktop causes display manager to freeze on startup"
date: 2015-09-01
forum: Desktop Environments
---

### Post by chellrose on 2015-09-01
I am running dual-boot Xubuntu 15.04/Win 7.  I tried to install KDE alongside xfce, but after installing KDE via
```
 sudo apt-get install kubuntu-desktop
```
 and rebooting, I find that the screen freezes.  It seems to freeze right as the display manager is trying to start up, so that the login screen never gets displayed.  Dropping to terminal and trying to start the display manager from there was unfruitful.  The only way I was able to access the graphical environment was by uninstalling kubuntu-desktop.

I later tried again, this time using Trinity DE (following the instructions found [here]("https://wiki.trinitydesktop.org/UbuntuInstall")).  Once again, the screen freezes and I can't login to the graphical environment or start the display manager.  I had to uninstall TDE to get my graphics back.

A point of note: When installing TDE, I told it to use Trinity's display manager rather than lightdm.  I haven't gotten brave enough to try it the other way around.  Also, on my old laptop, I had Xubuntu with Trinity installed alongside.  I think that was Xubuntu 14.10.  I had no problems with the install back then.

Is there a way to install an additional DE on 15.04 without breaking the display manager(s)?

Thanks.

---

### Post by CantankRus on 2015-09-02
Kubuntu appears to use sddm as the display manager in 15.04. 
The [**_[COLOR="#B22222"]sddm[/COLOR]_**]("http://packages.ubuntu.com/search?keywords=sddm&searchon=names&suite=all&section=all") package is only present in 15.04 up.

I have a test 15.04 ubuntu install that I installed **sddm** on and set it as the display manager.
All I get is a white screen at the greeter.

When installing kde or other desktops that install a different display manager, choose to keep **lightdm** as the display manager if prompted.
You can choose between different installed display managers with...
```
sudo dpkg-reconfigure lightdm
```

---

### Post by Bucky Ball on 2015-09-02
Perhaps better to install Kubuntu as installing kubuntu-desktop is the equivalent of installing Kubuntu on top of Ubuntu. With other desktops, this can work ok, although you will get redundancy and bloated menus, but KDE has some specific quirks that can make it unfriendly when attempting to do what you've done.

Doesn't help with your issue but something to keep in mind. 

PS: I have changed the title of your thread as you haven't installed a desktop environment, per se, but Kubuntu. Installing the desktop environment is installing KDE, not kubuntu-desktop. That is very different. If you wanted to install the Xubuntu desktop environment, xfce4, for instance, you install xfce4, NOT xubuntu-desktop. The latter drags in the entire OS pretty much.

---

### Post by chellrose on 2015-09-02
Thank you both.  I'll try again soon with keeping lightdm as the display manager and update my thread with the result.

Also, thanks for the tip on the install -- I've always been told to install KDE by installing kubuntu-desktop and I didn't realize I was installing a whole other OS!  That does seem a bit redundant.

---

### Post by CantankRus on 2015-09-02
You might find this [**_[COLOR="#B22222"]TIP[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2289043&p=13332591#post13332591") useful  when installing metapackages.

---

