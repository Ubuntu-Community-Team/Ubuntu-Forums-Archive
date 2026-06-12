---
title: "Gnome is broken, various things crashed"
date: 2013-02-17
forum: Desktop Environments
---

### Post by Scarberian on 2013-02-17
I have been trying to get my ASUS PCE-15N wifi card running and in the process it seems gnome has broken. After a reboot, the desktop starts up with a series of crashed. gnome power management, sessions some other thing, I have unity dash but Wicd won't run, I dont get any drop down at all from the power button in the tray, no audio drop down, now keyboard shortcuts. I dont knwo how to trouble shoot this.

I was installing a custom .deb pkg immediately before this and I was using sudo su. There was a warning about this but I dont know how serious it was. My desktop looks almost the same but no sound or internet.

EDIT:I am running Quantal Quetzal

When i run the system settings it opens but when i select networking it crashes instantly.

where to start?

---

### Post by aarons6 on 2013-02-18
you could start by making a new user and seeing if that one logs in ok..

if this is the case then your home folder has some messed up files..

i am betting what happened is while you were su you wrote some config files in your home folder as root.. 


this is why you NEVER sudo su.. 

if the new user logs in ok, you can try to chown all the files in your home folder to user:user
that might not work tho and you may have to delete them and have the system remake them.

---

### Post by Scarberian on 2013-02-18
I just did chown -R to my home folder and rebooted. No change. I looked in the .gnome folders but they didnt really contain much at all to delete. What am looking for and where might I look?

---

### Post by Scarberian on 2013-02-18
I installed the wireless drivers that i found here and then rebooted into this mess. [https://github.com/aptivate/linux-ischool-classmate](https://github.com/aptivate/linux-ischool-classmate)

I cant seem to get USB drives to mount and not internet from the machine. I will be able to try a wired connection soon but i wonder if even that will work.

Specifically:

git clone git://github.com/aptivate/linux-ischool-classmate.git
cd linux-ischool-classmate/rtl8192ce-dkms/r8192ce-0007.0809.2012-1~classmate~121102~1cw
debuild -i -us -uc -b
dpkg -i ../r8192ce_0007.0809.2012-1~classmate~121102~1cw_all.deb

---

### Post by Scarberian on 2013-02-18
All I can do is take pics to easily share info
dmesg | Greg error 
[http://imgur.com/ydS5CVN](http://imgur.com/ydS5CVN)
History right before the shutdown on line 921
[http://imgur.com/L4HiJ5p](http://imgur.com/L4HiJ5p)

---

### Post by meteorrock on 2013-02-18
yeah you do not do a sudo su with install. Looks like you will have to purge your gnome 3 setup and start over from scratch.

Run this command in the terminal.

 ```
sudo apt-get update
```
Code:
```
sudo apt-get purge alacarte cups-pk-helper gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6 gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-applets gnome-applets-data gnome-contacts gnome-icon-theme-full gnome-panel gnome-panel-data gnome-session-fallback gnome-shell gnome-shell-common gnome-themes-standard indicator-applet-complete libcaribou-common libcaribou0 libclutter-1.0-0 libclutter-1.0-common libcogl-common libcogl-pango0 libcogl9 libgjs0c libmozjs185-1.0 libmutter0 libpanel-applet-4-0 mutter-common python-gmenu
```

Also remove the gnome classic shell that comes with gnome 3.


```
sudo apt-get purge alacarte cups-pk-helper gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-panel gnome-panel-data gnome-session-fallback indicator-applet-complete libpanel-applet-4-0 python-gmenu
```


The above codes should totally purge all of that gnome shell along with its settings and other packages that go along with it. Source here. [http://askubuntu.com/questions/65200...-installing-it](http://askubuntu.com/questions/65200...-installing-it)



 ~~~~~~~~~~~~~

 Then try to re-install it and see if that helps. The new gnome 3 shell uses graphical hardware acceleration so if your computer specs are on the old side, it might not work correctly for you. 

 To reinstall it use these commands. 


```
sudo apt-get update && sudo apt-get install ubuntu-gnome-desktop ubuntu-gnome-default-settings
```

Its a good idea to uninstall the ubuntu settings also.


```
sudo apt-get remove ubuntu-settings
```

Then install optional settings for gnome 3 using ubuntu. 


```
sudo apt-get install gnome-documents gnome-boxes
```

The ppa, which you will want to keep gnome 3 updated is this code here. 


```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

Source here for the guide. [http://www.webupd8.org/2012/10/how-t...esktop-in.html](http://www.webupd8.org/2012/10/how-t...esktop-in.html)

 ~~~~~~~~~~~~

 Hope that helps.


Look online for another tool called "NISwrapper"  for your wireless card and its drivers.

---

