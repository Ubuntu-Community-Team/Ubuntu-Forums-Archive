---
title: "Broadcom Wireless (bcwml5.inf) Problems"
date: 2006-01-14
forum: General Help
---

### Post by upenox on 2006-01-14
I'm hoping someone could help me.  I'm trying to help a friend get wireless setup on his HP zv6130 notebook.  He's dual-booting, and under Windows his wireless adapter shows up as a Broadcom 802.11b/g.  So I did some searching and grabbed the bcwml5.(inf|sys) and got them onto his linux partition.  We uninstalled ndiswrapper-utils and erased the config files, etc. as it said in this thread:[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset+ndiswrapper+howto](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset+ndiswrapper+howto) .  

So I had him reinstall ndiswrapper-utils and had him do the following:
   sudo ndiswrapper -i ~/broadcom/bcmwl5.inf
   sudo ndiswrapper -m

Then I had him grep all of the *.conf files in /etc/ndiswrapper/bcmwl5/ for 'RadioState'.  All of the lines were already set to 'RadioState|0'.  So I had him reboot, and his wireless did not come up (as it says should in the thread mentioned earlier).  So we ran a 'modprobe ndiswrapper', and still got nothing.  I then had him then do a 'ndiswrapper -l' and it's supposed to say:

"bcmwl5 driver present, hardware present"

but all it says is:

"bcmwl5 driver present".

Can anyone think of a reason why the 'hardware present' isn't showing up?

Thanks! :) 

-upen

---

### Post by kolesarm on 2006-04-22
i have the same problem. no diea what to do...

---

### Post by kolesarm on 2006-05-05
I finally got it working properly about a week ago. the trick was to use a different bcwml5.inf file - the one that came with the cd. alternatively, trying [the ndiswrapper homepage]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") and taking it from there might help too.

---

### Post by MrMojoRising on 2006-05-05
Fix it?

---

### Post by got_nix on 2006-05-05
[QUOTE=kolesarm]I finally got it working properly about a week ago. the trick was to use a different bcwml5.inf file - the one that came with the cd. alternatively, trying [the ndiswrapper homepage]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") and taking it from there might help too.[/QUOTE]
omg i really realy really hope this works yknow... i've been going without wifi for a bout 2 weeks in ubuntu and i'm sick of it. right now i have to be in windows :( at a friends house to use there wifi.. gonna try this method will let ya'll know if it works.

---

### Post by evlutn on 2006-05-06
Having had to suffer from the same problem, I finally got my Broadcom wireless card working.  The following instructions worked for me.  I'm still learning, having just converted to Linux two weeks ago.  I'm not yet knowledgeable enough to know the reason for all the steps, but my wireless card is working, so I don't care!!  Here's what you do:

Make sure that you have the Windows drivers.  I have an Acer Aspire 3000, so I downloaded mine from Acer's site.

1.  Create a broadcom folder in your Home folder.
2.  In the folder, add both the bcmwl5.inf and bcmwl5.sys files.
3.  In Terminal type: cd /home/your user name/broadcom
3.  Type: sudo ndiswrapper -i bcmwl5.inf
4.  Type: sudo ndiswrapper -d 14e4:4318 bcmwl5
5.  Type: sudo ndiswrapper -l and it should say -- bcmwl5 driver present, hardware present
6.  Type: sudo depmod -a
7.  Type: sudo modprobe ndiswrapper

From here, go to Networking and activate the card.

Go back to the terminal:

sudo iwconfig wlan0 essid "your network name" e.g. sudo iwconfig wlan0 essid wireless
sudo iwconfig wlan0 mode managed

After those, then do the following in order:
sudo ifconfig wlan0 up
sudo dhclient wlan0

Once you're connected, you type:
sudo ndiswrapper -m

Hopefully, everything should be working.  If it doesn't, I can probably help you.  I've played around with several Linux distros and I got the card to work in every single one when I followed the instructions I just gave you.

Good luck,

Angel

---

### Post by jshein on 2006-05-07
Some Acers ( Like my TravelMate 4400 ) require the acer_acpi drivers in order to make the wireless function, due to the fact that these laptops boot with the card physically disabled.

You can get acer_acpi here
[http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)

To install it:
#wget [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
#tar zxvf acer_acpi-0.3.tar.gz
#cd acer_acpi-0.3
#make
#sudo make install
#sudo modprobe acer_acpi

now check if the module loaded properly
#dmesg | grep acer_acpi

I use the script at the bottom of this post to enable the card. The script has been midified from its original version to enable it to work properly on Ubuntu. 
Save this script as /usr/bin/acerwl

Then change the permissions on the script
#chmod 755 /usr/bin/acerwl

Edit /etc/sudoers to allow users to enable the wireless using the script

#sudo visudo
Add the following to the bottom:

```

#ndiswrapper for acer
%users  ALL=(ALL)       NOPASSWD: /usr/bin/acerwl

```


script for /usr/bin/acerwl :

```

#!/bin/bash
#
# Copyright Francois Wautier 2005
# A script tp toggle the wireless adapter on Acer 5020 Series laptop 
# This script is provided as-is, without any warranty.
# Permission is granted to use and abuse this script as
# long as the original copyright is mentioned
#
# Interface to use
interf=wlan0
#
# Module to us
wmodule=ndiswrapper
#
#
isloaded=`lsmod|awk '{ print $1 }'|grep $wmodule`
#
acerok=`lsmod|awk '{ print $1 }'|grep acer_acpi`

if [ "$acerok" == "" ]; then
	echo "acer_acpi not loaded. Attempting to load"
	/sbin/modprobe acer_acpi
	/sbin/modprobe acer_acpi
fi

acerok=`lsmod|awk '{ print $1 }'|grep acer_acpi`
if [ "$acerok" == "" ]; then
  	echo "Could not load acer_acpi. Aborting"
	exit
fi


if [ "$isloaded" == "" ]; then
	#Load it
	# Enable the radio
	echo "enabled : 1" >/proc/acpi/acer/wireless
	sleep 4
	# Load the driver. Hotplug should do the rest
	/sbin/modprobe ndiswrapper
	sleep 4
        /sbin/ifup wlan0
else
	/sbin/ifconfig $interf down
	#/etc/init.d/net.$interf stop
	echo "enabled : 0" >/proc/acpi/acer/wireless	
	/sbin/rmmod ndiswrapper
        # Enable the radio
        echo "enabled : 1" >/proc/acpi/acer/wireless
        sleep 4
        # Load the driver. Hotplug should do the rest
        /sbin/modprobe ndiswrapper
        sleep 4
        /sbin/ifup wlan0
fi

```

Good luck. Worked for me after many hours of frustration.

---

### Post by nickm on 2006-06-01
try [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) <- That :)

---

### Post by Jbweld on 2006-12-06
IN TERMINAL Program...
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome
sudo apt-get
sudo apt-get install wpasupplicant
--------------------------------------------------------------------------
sudo gedit /etc/network/interfaces
# Comment out everything other than “lo” entries in that file and save the file 
USE # to comment out!
((Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
Sudo Gedit /etc/default wpasupplicant))) add ENABLE=0 into it and save file.
-----------------------------------------------------------------------------
sudo touch /etc/default/wpasupplicant
YEAH RE_Boot
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
Then set it all up with wpa/network names etc..

---

### Post by itsjustarumour on 2007-01-08
> **evlutn said:**
> Having had to suffer from the same problem, I finally got my Broadcom wireless card working.  The following instructions worked for me.  I'm still learning, having just converted to Linux two weeks ago.  I'm not yet knowledgeable enough to know the reason for all the steps, but my wireless card is working, so I don't care!!  Here's what you do:

Make sure that you have the Windows drivers.  I have an Acer Aspire 3000, so I downloaded mine from Acer's site.

1.  Create a broadcom folder in your Home folder.
2.  In the folder, add both the bcmwl5.inf and bcmwl5.sys files.
3.  In Terminal type: cd /home/your user name/broadcom
3.  Type: sudo ndiswrapper -i bcmwl5.inf
4.  Type: sudo ndiswrapper -d 14e4:4318 bcmwl5
5.  Type: sudo ndiswrapper -l and it should say -- bcmwl5 driver present, hardware present
6.  Type: sudo depmod -a
7.  Type: sudo modprobe ndiswrapper

From here, go to Networking and activate the card.

Go back to the terminal:

sudo iwconfig wlan0 essid "your network name" e.g. sudo iwconfig wlan0 essid wireless
sudo iwconfig wlan0 mode managed

After those, then do the following in order:
sudo ifconfig wlan0 up
sudo dhclient wlan0

Once you're connected, you type:
sudo ndiswrapper -m

Hopefully, everything should be working.  If it doesn't, I can probably help you.  I've played around with several Linux distros and I got the card to work in every single one when I followed the instructions I just gave you.

Good luck,

Angel

Evlutn - Thanks for a fantastic "how-to", this worked first time for me with a USR5417 MAXg card and USR9108 wireless router on Edgy 6.10 32bit!!  =D>  (had to reboot my machine after btw). For info I downloaded the bcmwl5.inf and bcmwl5.sys files from another post at [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=4318)  where it says "this file"...

---

### Post by itsjustarumour on 2007-01-20
> **evlutn said:**
> Having had to suffer from the same problem, I finally got my Broadcom wireless card working.  The following instructions worked for me.  I'm still learning, having just converted to Linux two weeks ago.  I'm not yet knowledgeable enough to know the reason for all the steps, but my wireless card is working, so I don't care!!  Here's what you do:

Make sure that you have the Windows drivers.  I have an Acer Aspire 3000, so I downloaded mine from Acer's site.

1.  Create a broadcom folder in your Home folder.
2.  In the folder, add both the bcmwl5.inf and bcmwl5.sys files.
3.  In Terminal type: cd /home/your user name/broadcom
3.  Type: sudo ndiswrapper -i bcmwl5.inf
4.  Type: sudo ndiswrapper -d 14e4:4318 bcmwl5
5.  Type: sudo ndiswrapper -l and it should say -- bcmwl5 driver present, hardware present
6.  Type: sudo depmod -a
7.  Type: sudo modprobe ndiswrapper

From here, go to Networking and activate the card.

Go back to the terminal:

sudo iwconfig wlan0 essid "your network name" e.g. sudo iwconfig wlan0 essid wireless
sudo iwconfig wlan0 mode managed

After those, then do the following in order:
sudo ifconfig wlan0 up
sudo dhclient wlan0

Once you're connected, you type:
sudo ndiswrapper -m

Hopefully, everything should be working.  If it doesn't, I can probably help you.  I've played around with several Linux distros and I got the card to work in every single one when I followed the instructions I just gave you.

Good luck,

Angel

Hi again  :) 

Well, I should never have tried to install Compiz/Beryl on a working system - after a week of abject pain and misery I've had to do a fresh install.  So I've come back here for your excellent how-to... and this time its not working!  Everything seems to go just as it should until right at the end, when I do
```
sudo dhclient eth1
```
(my connection is "eth1" btw) and I get:
```
ian@COOLERMASTER:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:c0:49:f7:77:ed
Sending on   LPF/eth1/00:c0:49:f7:77:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
I've tried rebooting etc but no joy - any ideas?  My wireless setup seems fine, I can boot back into WinXP and no probs!

---

