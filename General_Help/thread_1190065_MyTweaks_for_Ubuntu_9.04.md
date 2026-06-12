---
title: "MyTweaks for Ubuntu 9.04"
date: 2009-06-17
forum: General Help
---

### Post by tuxhats on 2009-06-17
Due to my career position, Computer Science teacher at a local High School, I have provided this tweak for students to follow or lastly, do myself. Enjoy!
;)

Installaton, partitioning, dual booting, and visudo help is included.

How to install Flash, java6jdk, g++, limewire, wireless config, gstreamer, ssh, OpenOffice, Games, and set-up through synaptic. How-to-tweak your version. Customize.

---

### Post by tuxhats on 2009-06-17
Hope this text file will help users setup Ubuntu for their needs 
Enjoy ;)

Installaton, partitioning, dual booting, and visudo help is included.

How to install Flash, java6jdk, g++, limewire, wireless config, gstreamer, ssh, OpenOffice, Games, and set-up through synaptic. How-to-tweak your version.

---

### Post by Legace on 2009-06-17
Reposted (you have to do right-click -> save as to open the file).

```
		    My_Tweaking of Ubuntu for the Desktop

Ubuntu 9.04 Installation:
Download Ubuntu 9.04 Desktop LiveCD from a mirror, say:
    http://ubuntu-mirror.cs.colorado.edu/releases/jaunty/ubuntu-9.04-desktop-i386.iso
		OR  pick your own at:
    http://www.ubuntu.com/getubuntu/download/
Burn this download "iso" as an image(iso image) on your cd. Google for help, if necessary:
    Search for "How to burn an iso image" to get some idea how.

**************
If planning on Dual Booting with any MS OS(XP,Vista,etc) , defrag the hard drive first!
Second, backup all of your important stuff on some other device or media.
Third, some MS OSes have a way to resize themselves,....maybe.

NOTE: If the Hard Drive is locked so resizing above isn't possible!
	Find a new installation MS cd of your choice.
	Get working license keys for this CD! You will then follow the dual
	booting instructions further below to install MS on 1/2 the hard drive.

**************
To Boot Ubuntu LiveCD (Use of F1 thru F12 keys, DEL, or ESC to access the "bios" boot menu
    if necessary to adjust the booting order.) I.E. -> Hard drive, CD/DVD, floppy, etc.

Press "Enter" for English if appropriate for you.
Press "Enter" to "Try Ubuntu"
    Let the boot-up continue to your desktop is complete.
    
Notice, once you are booted up, in the upper left corner of your desktop, "Applications",
"Places", and "System". Under "System", choose "Administration", and then choose 
"Partition Editor".

###### FOR A NON-DUAL Booting Partition Setup with Ubuntu [ Your Best Option! ] ######
   The Objects using Partition Editor: 
	Delete all existing partitions.
	We want to make 3 new partitions; (We want our drives to have numbers like,
	    /dev/sda1, /dev/sda2, and /dev/sda3, NOT /dev/sda4, /dev/sda5, /dev/sda6.)

	1st Partition, make the partition "Primary", and the file type -> reiserfs,
	    make the mount point "/" for /dev/sda1. Use about 25GB(25000MB) 
	    or 30GB(30000MB).
	2nd Partition, make the partition "Primary", and the file type -> reiserfs,
	    make the mount point "/home" for /dev/sda2. Use ALL but 1200MB at the end.
	3rd Partition, make the partition "Primary", and the file type -> swap area,
	    for /dev/sda3 with no mount point. Use the remaining 1200MB.
   Apply these steps by clicking on the "Apply" (check-mark) icon. 
   Then close the Partition Editor.
	Continue thru installation.

###### If Dual Booting with any MS OS(XP,Vista,etc) ######
For Dual Booting, go to the links near the bottom of this web page, for all MS types.
   http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm
If MS won't let yo resize your hard drive;
	Boot Ubuntu, Got to "System", then choose "Partition Editor".
	Delete all partions.
	Object Now: Make 2 partitions.
		1st Partition make the file type -> ntfs and use 1/2 your hard drive.
		2nd Partition make the file type -> ext3 for now
	Install your MS os CD using the 1st partition ONLY for it.
	Boot Ubuntu, begin installation.
	Upon the choice of partitioning options, choose "Manual" option!!!
	Choose the non-ntfs hard drive, and create a new "primary" partition.
	Make its size all but 1200 MB at the end, make it a reiserfs file system type.
	Create a new "primary" partition, make it a "swap area".
   Apply these steps by clicking on the "Apply" (check-mark) icon. 
   Then close the Partition Editor.
	Continue thru installation below.

######
Now, on the desktop is the "Install" icon. Double Click. Follow the installation through.
If appropriate for you and your area of the world, language, etc.;
Choose "English", then "Forward" to the next page. Set "Region: America" and "City 
Chicago", Forword and then again throught the keyboard setup. Under the 
next page, "Prepare disk space", choose(check) the 'radio button' next to the
"Specify partitions manually(advanced)" choice!!!!! Then forward.

Under the new page, "Prepare partitions", click on the 1st partition
(/dev/sda1) and select "Edit partion" below. Change "Use as:" to "ReiserFS ..."
and the "Mount point:" as " / ". Check the "Format the partition:" checkbox. "OK".
    Edit the 2nd the partion to be formatted as "ReiserFS" and the "Mount point:" as
	" /home ". OK. 
    Choose the 3rd partition to edit. Choose to "Use as: swap area". OK.

Now choose, "Forward" to continue to the next installation page. 
On the next page, "Who are you?", fill it out, making sure there are no spaces
in a username and is lowecase. Decide on a password. Forward, then choose "Install". 
Continue with the installation and reboot the computer after the install. 
Enter your username <enter> then your password<enter> to take you to the desktop.
You are now ready to make tweaks/adjustments to your new installation as I have
suggested below.

********** Post Installations Below Are Optional ********** 
Add Multiple Desktops:
In the lower right corner, there are 2 small squares representing each desktop. Move
    your mouse over them and right click, choose "preferences". Change, in the new 
    small window that pops up, change "Columns" from 2 to 4. Close.
    
**********
Visudo Setup (gives us some extra root privileges we need on occasion)
Click on "Applications -> Accessories -> Terminal (also know as a "shell")
    type: sudo visudo    then <enter>
    enter: your password   then <enter>
Use your down arrow keys to move below:
    root    ALL=(ALL) ALL	and add yourself
    jim     ALL=NOPASSWD: ALL
Then use your arrow keys to move further down to:
    #%sudo ALL=NOPASSWD: ALL	and remove the # sign in front of this line.
Press CTRL and X together to exit. Type "y" to save changes.

**********
Synaptic(Our package manager)
Note: Try to always use this tool first to add any software!!!!!!!!!!

Under "System" in the upper left of your desktop, choose "Administration", and
then choose "Synaptic Package Manager". Type in your password. In our new window, find
"Settings" and choose and then "Repositories". In this new window, we are going to
work with the first 3 tabs at the top. They are:
    "Ubuntu Software", "Third-Party Software", and "Updates".
Under our first tab on the top left, check the first 4, leaving "source" unchecked.
On the next tab, check the first one on top. On our final tab, 
check the first 4 at the top AND UNCHECK THIS ONE: "Check for updates"!!!

NOTE: I don't always think a newbie should do regular updates w/o an experienced Linux 
person around as the community makes some mistakes and this isn't good for newbies.
Example: For whatever reason ctrl + alt + back_space has been disabled in the updates of
Ubuntu 9.04. You can get it back by installing "dontzap" through synaptic and running
the following in your shell:
    dontzap --disable
 
Close this window and then choose "Reload" after you return to the main window of
Synaptic. Expand this window so that you can clearly see the "Search" button. Ignore
the "Quick search" which is for searching already installed software.

    Search for: 
	Java6 -> install sun-java6-jdk and sun-java6-plugin
		(right click on the file and "Mark for Installation" and
		    continue through by choosing "Mark" in the new window)
	g++ -> install g++  (same process as above)
	flash -> install flash10   (same process as above)
	ssh -> install ssh  (same process as above)
	OpenOffice -> install openoffice.org   (same process as above)
Optional:   WINE    (same process as above)
    To Add Games, or other software...
	Click on the "Sections" button. Scroll down to the "Games and Amusement" 
	section and click on it to see the files available. Your call to add
	and remove them as needed.
When all of the above is completed then click on the "Apply" button. At this time,
expand this NEWEST window by finding the little arrow pointing to the right and 
'click' on it. This will further expand our current window. When prompted with a 
question, press your keyboard <enter> key. Continue as necessary.
Some softwares, ex. Java, require an agreement "OK" to continue OUR INSTALLATION!
Then click the "Close" button when this part is finished.
You may now close Synaptic by clicking on the "X" in the upper right corner of 
this(Synaptic Package Manager) window. 
    
**********
Install Limewire:   (for music downloads)
    http://www.limewire.com/download/releases/4.18.8   ... choose Linux download.

**********
Wireless configuration:
If Ubuntu doesn't set it up for you. You may wish to Google your wireless device.
I've included a list of useful links at the bottom of this file for additional help.
    
The link below if you unfortunately have a BroadCom device.
For BroadCom Wireless drivers (HP.....)
	http://ubuntuforums.org/showthread.php?t=769990	

To find your type of wireless card,
In a terminal, enter:
	lspci
MY SAMPLE:
jim@my-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1c:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
1c:03.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
1c:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
jim@my-laptop:~$ 

NOTE: Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI 
    Express Adapter. This is my wireless card! Fortunately it's not a "Broadcom".

**********
Playing DVD Movies:
	https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html

**********
To get gstreaming to work for wmv file types, etc:
Use synaptic and search for "gstreamer".
    I have the following files installed;
	bluez-gstreamer
	gnome-app-install
	gnome-codec-install
	gnome-media
	gstreamer0.10-alsa
	gstreamer0.10-ffmpeg
	gstreamer0.10-gnomevfs
	gstreamer0.10-pitfdll
	gstreamer0.10-plugins-bad
	gstreamer0.10-plugins-bad-multiverse
	gstreamer0.10-plugins-base
	gstreamer0.10-plugins-base-apps
	gstreamer0.10-plugins-plugins-good
	gstreamer0.10-plugins-ugly
	gstreamer0.10-plugins-ugly-multiverse
	gstreamer0.10-pulseaudio
	gstreamer0.10-schroedinger
	gstreamer0.10-tools
	gstreamer0.10-x
	libgstreamer0.10-0
	libgstreamer-plugins-base0.10-0
	openoffice.org
	pidgin
	pulseaudio
	python-gst0.10
	soundconverter
	totem
	totem-gstreamer
	ubuntu-restricted-extras

**********    
Get different Wallpapers:
   http://allforlinux.blogspot.com/2008/09/how-to-get-different-wallpapers-on-each.html

##########################################################################    
########### Just in case you are interested in 3-D manipulation ##########
FOR 3-D Animation:   
	http://ubuntuforums.org/showthread.php?t=17359
	
  OR follow details below.

  *** 
Open a shell,	then type->  	gconf-editor   then <enter>.
	Expand "apps", scroll down to "nautilus", expand it. Click on "preferences".
	In the right window pane, scroll down to "show_desktop", uncheck for now  ...
	(Return here later to recheck if desired after adding 3-D cube)
	Close this "Configuration Editor" by clicking pn the "X" in the upper right corner.

In Terminal, input the following:
	sudo apt-get install compizconfig-settings-manager

Go to System --> Preferences --> Advanced Desktop Effects Settings
	Tick "Desktop Cube" and opt to disable desktop wall if prompted
	Tick "Rotate Cube"
	Select "Desktop Cube"

OPTIONAL CHOICES AVAILABLE BELOW:
	Click "Appearance" tab
	Click "Add" under the "Background Images" field
	Browse for your desired wallpaper(s), ordering them based on which face of the cube
	you want them to appear.
	
	Return to *** area above, rechecking "show_desktop" if desiring the Return of the
		"Desktop icons".

END OF 3-D ANIMATION

**********
Additional and perhaps useful links:

http://ubuntuforums.org/
http://ubuntuforums.org/showthread.php?t=17359
http://www.google.com/search?q=Ubuntu+9.04+make+desktop+cube+work&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a
http://guevara2012.wordpress.com/2008/04/21/instalando-bcm94311mcg-wlan-mini-pci-no-ubuntu/
http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/
http://ubuntuforums.org/showthread.php?t=767833&highlight=crash+totem+avi&page=8
https://help.ubuntu.com/community/Repositories/Ubuntu
http://lifehacker.com/400505/rotate-desktop-backgrounds-in-ubuntu
http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/
    
**********
```

---

### Post by overdrank on 2009-06-17
Hi and welcome, please do not create multiple threads. Threads merged :)

---

### Post by tuxhats on 2009-06-17
Thank you fixing my posts and the merge!!! Wasn't sure how to post attachment other than paste. Thanks, hope this helps many!

---

