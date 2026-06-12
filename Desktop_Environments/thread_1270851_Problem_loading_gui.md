---
title: "Problem loading gui"
date: 2009-09-20
forum: Desktop Environments
---

### Post by daniel930123 on 2009-09-20
hi everyone
i got some trouble loading my GUI, the reason i got this is beacose i installed the mint gloria menu style and options in my dell mini 10's netbook remix of ubuntu, using these repos deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria main upstream import
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria backport
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria community
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria romeo
in the package list /etc/apt/sources.list after i putted these on the terminal sudo apt-get update
sudo apt-get install mintmenu

As i didn´t noticed the effects taking place after one reboot i tryed to install some drivers that wasn't installed (intel GMA 500 driver).
i tryed this part of a tutorlal to install them

From the Terminal:
Add this to your repository
Code:
sudo nano /etc/apt/sources.list.d/ubuntu-mobile.list
add these 2 lines

Code:
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
then ctrl+o (which saves it)
Then ctrl+x (To Exit)

Now you need to authenticate the keys

Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30
[/code]Now that your Ubuntu-Mobile Key is added do the Following.

The Following Packages need to be Installed Most are Dependences.

* psb-firmware - Binary firmware for the Poulsbo (psb) 3D X11 driver
* psb-modules - Kernel module built for -generic or -lpia kernel
* psb-kernel-source - Kernel module for the Poulsbo (psb) 2D X11 driver
* psb-kernel-headers - Kernel module headers for the Poulsbo (psb) 2D X11 driver
* xpsb-glx - X11 drivers for Poulsbo (psb) 3D acceleration
* poulsbo-driver-3d - Metapackage for the 3D Poulsbo (psb) X11 driver.
* poulsbo-driver-2d - Metapackage for the 2D Poulsbo (psb) X11 driver.



From a Terminal (this should install all the above):
Code:
sudo apt-get update
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d psb-firmware

till this step the installation appeared to be succesfull. 
but after the reboot, my OS didn`t charged the GUI (it appears to be the xorg server or the graphics driver, beacose it seems to replace GNOME with KDE GUI) obviusly, i couldnt finish the driver install succesfully, beacose of the GUI problems, also i tryed to re-install the whole OS with the disc image floppy.but the installer doesn't appears to affect installed OSs'.
the following steps on the tutorial are these:

Once rebooted open a terminal and make a back up of your xorg.conf file.(fresh install may have a null xorg.conf file this is normal and ok)

Code:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
Open up your xorg.conf and add the below contents inside it.
Code:
sudo nano /etc/X11/xorg.conf
Make the Section "Device" Look like this :

Code:
Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
EndSection
(Optional) add the following to the bottom of your xorg.conf file this will allow you to be able to do a CTRL+ALT+Backspace to restart your GUI/X11 session.

Code:
Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
Add the following Line at your risk. It could have mixed results. Ive have very good luck thus far performance wise with it.
Code:
        "AccelMethod" "UXA"
Reboot one last time and you should be rocking and rolling. Now what this did is allow the 3d Drivers to be installed and are in Partial use. Compiz and any other 3d Software "May" Not work I haven't 100% tested it. But modifying your xorg.conf with the above setting will allow you to be able to use External USB Devices with out random freezes.

If you have a fresh install you may need to recheck your xorg.conf file after you reboot as when the xserver configures itself it may put back the default settings. Those that had xserver setup before hand you should be fine. But if you feel that something isnt right, you may want to go and check your xorg.conf file again and be sure that the options are still there.

Leave out the xorg.conf if you don't plan on using anything USB. Although since your keyboard / touch-pad is technically USB I still had random Freezes Have 3d Enabled.

So I Highly Recommend using my xorg.conf example. I have had great success with it.

For those who are getting DRM errors after Upgrading from / to a new Kernel after doing the Old Procedures I had listed here do the following.

Code:
sudo apt-get install psb-kernel-source

does it has simething to do that i didn`t finished the installation?
im sorry if my problem is quite dum, but im new to linux, and im still gettind used to it. TNXS

---

