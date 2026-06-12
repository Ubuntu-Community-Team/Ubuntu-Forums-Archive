---
title: "What is the process to install Seamonkey Suite in Ubuntu 804?.."
date: 2009-01-21
forum: Desktop Environments
---

### Post by DonaldJ on 2009-01-21
Am running 804, Compaq Presario, 75-gig hd, 1-gig Ram... 

What is the process to install SeaMonkey Suite in Ubuntu-804..?  I have tried and tried and tried...  It's giving me gray-hairs..  and I've learned two new cuss-words too...

I just switched over from Windows...  I'm hooked on SeaMonkey Suite's compose-features...  Getting away from Windows gives the feel like I finally got microsoft's claws out of my throat, and msn's finger out of my private place...  

Microsoft should be bankrupt 14.7 years from now...  Will be good to see the bully go...


I go to the SeaMonkey download-page, and paste the key into repository, but the "add source" doesn't highlite..?   I'm stuck...:(

---

### Post by opscure on 2009-01-21
Download the SeaMonkey installer from this link:
[http://download.mozilla.org/?product=seamonkey-1.1.14&os=linux&lang=en-US]("http://download.mozilla.org/?product=seamonkey-1.1.14&os=linux&lang=en-US")


To install SeaMonkey by downloading the SeaMonkey installer, follow these steps:

1. Create a directory named seamonkey (mkdir seamonkey) and change to that directory (cd seamonkey).
	
2. Click the link on the site you're downloading SeaMonkey from to download the installer file (called seamonkey-x.xx.en-US.linux-i686.installer.tar.gz or similar) to your machine.

3. Change to the seamonkey directory (cd seamonkey) and decompress the archive with the following command:

  tar zxvf sea*.tar.gz

The installer is now located in a subdirectory of seamonkey named seamonkey-installer.

4. Change to the seamonkey-installer directory (cd seamonkey-installer) and run the installer with the ./seamonkey-installer command.

5. Follow the instructions in the install wizard for installing SeaMonkey.

Note: If you have a slower machine, be aware that the installation may take some time. In this case, the installation progress may appear to hang indefinitely, even though the installation is still in process.

6. To start SeaMonkey, change to the directory where you installed it and run the ./seamonkey command.



To hook up SeaMonkey complete with icon to the GNOME Panel, follow these steps:

1. Click the GNOME Main Menu button, open the Panel menu, and then open the Add to Panel submenu and choose Launcher.

2. Right-click the icon for SeaMonkey on the Panel and enter the following command:
  directory_name./seamonkey

where directory_name is the name of the directory you downloaded SeaMonkey to. For example, the default directory that SeaMonkey suggests is /usr/local/seamonkey.

3. Type in a name for the icon, and type in a comment if you wish.

4. Click the icon button and type in the following as the icon's location:

  directory_name/icons/mozicon50.xpm

where directory name is the directory where you installed SeaMonkey. For example, the default directory is /usr/local/seamonkey/icons/mozicon50.xpm.

---

### Post by DonaldJ on 2009-01-22
Thanks...


Oyie!  No-wonder I couldn't get SeaMonkey to install... 

I've been using Linux only for 48-hours now..  this is gonna be a bit of a learning-curve sterrretch, especially trying to find where to paste those keys.. oh sigh...

Like learning to ride a bike that's two-sizes too big for you..  or like   learning to swim, alone...

Why aren't there installers for Ubuntu peripheral-softwares..?

---

### Post by opscure on 2009-01-26
how did that process go for you.  Sorry, I didn't realize that you were so new.  You may just want to click applications on your toolbar and go to add/remove...  from there you can just search for seamonkey and you should be able to just click and install.

As for your other questions:
There are usually installers for most software you would need for ubuntu, it is pretty user friendly.  You just need to know where to look.  Also, any file that is packaged for debian in the form of a .deb file will work with a double click like a windows machine.

I'm not sure what you are referring to in regards to seamonkey on a self bootable cd. Usually a bootable cd requires some form of kernel or os to boot into first, seamonkey is an application not an operating system.

Any computer system can be hacked or destroyed.  Ubuntu/.nixes are no exception; however, it is less likely that your system will be hacked/destroyed as often as say a windows system.  The most probable case of your system becoming unusable is configuration errors or kernel modifications outside the realm of the distributed/accepted updates put out by the development team.... ie user error.

---

### Post by oldos2er on 2009-01-26
Or open a terminal and enter

 ```
sudo apt-get update && sudo apt-get install seamonkey
```

---

