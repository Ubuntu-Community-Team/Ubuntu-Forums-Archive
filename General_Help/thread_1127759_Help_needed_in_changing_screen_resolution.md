---
title: "Help needed in changing screen resolution"
date: 2009-04-16
forum: General Help
---

### Post by hurstdaj on 2009-04-16
I've been having this problem for a few days now.  I have an older graphics card the nvidia Geforce 4 mx series.  When I was running windows, I never had a problem getting a screen resolution of 1024X768.  I need to get this resolution back.  With Ubuntu, the highest option it is giving me is 800X600.  I was able to find the correct driver from the nvidia website and installed it using sudo sh.  Everything appeared to install with no problem, but I still can only get 800X600.

What can I do to change this?  For the most part I love what I see with Ubuntu.  I really hate Windows, but this screen resolution problem may make me go back.  Can anyone help with this problem?

---

### Post by upchucky on 2009-04-16
Ubuntu 8.04 is a long term supported release meaning most nvidia cards will work.

since you have an older card, you may have to do a bit of searching on nvidia site for the right linux driver for your card, it could very well be one of the legacy drivers.

8.10 is not a long term release, and some reports say the nvidia cards will work, however there are tweaks to get it working. 

when you have confirmed that you have the right driver, the following is the proper way to set up nvidia when using 8.04

there are other ways like Envy, but they are workarounds and usually do not set up selectable resolutions and other things that the card is capable of, plus they do not work on every machime.

if you are using Ubuntu 8.04 and the live cd boots into graphical then do this,



Set up Nvidia driver

Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     [http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

---

### Post by wrose51106 on 2009-04-16
Sytem > admin> synapteic package manager, install the latest Nvidia drivers 180.xx or so. Reboot and away you go. I do not bother to install anything unless it i through package manager myself, best of luck.

-been drinkin Bill

---

### Post by hurstdaj on 2009-04-16
Thanks upchucky I'll try that way and post with the results.  

I haven't had any success through package manager either.  The driver that is being installed that way is worse.  640X480 is the highest available.

Edited:  I am actually running version 8.10  How do I change it to 8.04?

---

### Post by upchucky on 2009-04-17
you can try it with version 8.10, someone has done this in the testing thread i created for 8.10 and reported success.


to change to 8.04, you would need to download 8.04 and burn it to cd then install.

however I am interested in any results of people trying to install on 8.10
hint, hint.

---

### Post by CatKiller on 2009-04-17
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

---

### Post by DJonsson2008 on 2009-04-17
catkiller's method is a lighter touch method that has worked
where other methods have failed, thanks catkiller. 

in fact i've found with the generic vesa drivers i'm able 
to get the better easier on my eyes refresh rates and
the 1024 wide screen i need.

i don't know why the nvidia drivers can be so tough to get
going, but it seems either they work or they don't and if
they don't it may be hard to roll back to older nvidia
drivers without a complete reinstall.

but if the nvidia drivers are not working the vesa drivers
seem functional and robust. 

be sure before you begin rock and rolling with nvidia driver
installs to be ready to manually backup and restore your 
xorg.conf from the command line.

i'd suggest getting your resolution working using a manual
edit to your xorg.conf file first with vesa drivers before
testing your luck with nvidia, then if nvidia either breaks
or does not work you can roll back to vesa.

---

