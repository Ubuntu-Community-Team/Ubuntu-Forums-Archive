---
title: "Strange problem with my custom wireless networking script"
date: 2006-07-12
forum: Desktop Environments
---

### Post by bensexson on 2006-07-12
I have a custom script I use to scan for possible known WAPs and to then set up my interfaces file to connect to the found WAP.  It works except for one strange issue.  Here is the script:
#! /bin/bash

declare -a networks	# array to hold profile names
declare n=0		# variable to hold counter
declare AP		# variable to hold MAC of AP

networks=(`ls /etc/network/test | cat`)	# populate array netwoks with profile names

/sbin/modprobe ndiswrapper # load ndiswrapper
/sbin/iwconfig eth1 essid any enc off
 
until test -z ${networks[n]}	# loop until networks returns a null
do
	/etc/network/test/${networks[n]}	# run iwconfig with settings for each network
	sleep 1	# sleep until wireless is set
	AP=`/sbin/iwconfig eth1 | grep Not-Associated -o`	# test if AP MAC is default meaning no connection
	if test -z $AP	# if variable AP is null we have a connection so set interfaces to link to correct profile and exit
	then
        	/bin/rm -f /etc/network/interfaces
        	/bin/ln -s /etc/network/profiles/${networks[n]} /etc/network/interfaces
		exit 0
	fi
	let n+=1
done

/bin/ln -s /etc/network/profiles/none /etc/network/interfaces # set profiles to none


This works with one strange issue.  The script makes a symbolic link to an interfaces file based on the WAP it finds.  Then I rely on the rest of the bootup process to bring up the network.  This all works.  But if it boots to runlevel 5 somehow the symbolic link is being changed to the first profile in the list.  The correct wireless settings are made and I will be connected to the WAP but if I use ifdown and up it will of course use the incorrect interfaces file because the symbolic link has been changed to the incorrect file.  Now if I run this script after booting or use the recovery boot it all works correctly.  So with a normal boot something is changing the symbolic link to the first profile in the profiles directory.  I do not know how to see what is happening during bootup.  Is there a way to have this script log so I can see what is happening?

---

### Post by bensexson on 2006-07-12
bump

---

### Post by bensexson on 2006-07-12
bump

---

### Post by KingBahamut on 2006-07-20
Im going to try to reproduce this on my Dell Latty at home, you mind if I borrow this script and see? Ill tell you what I find out when im done with it.

---

### Post by bensexson on 2006-07-22
Don't mind at all.  You will need to create multiple interfaces files in /etc/network/profiles and the  scripts to set iwconfig in /etc/network/test.
This script sets iwconfig for each of the possible networks and tests the associated AP field of the iwconfig output.  If it finds a network that does not return Not-Associated in this output it is supposed to create a symbolic link for /etc/network/interfaces the appropriate profile file.  What has been happening is it detects the correct network by the symbolic link is not the correct one by the end of booting.

---

### Post by bensexson on 2006-07-22
My real problem is I don't know how to disable usplash so I can print messages to the screen and see what is going on.

---

### Post by bensexson on 2006-07-25
Thanks, for the reply KingBahamut.  I was able to fix the problem.  I needed to add sleep 1 after modprobing ndiswrapper to allow the module to fully load.

---

### Post by randell6564 on 2006-07-25
Hey folks!

UH... I would like to use this script.  The thing is, I dont know where to put it in order for it to execute.

Can you help?

Thanks!

---

### Post by bensexson on 2006-07-25
This is a script I made myself.  It will take a little modification to get to work.  Also it is intended to work with ndiswrapper and eth1 for the interface name and will only work with WEP.  This is because the wireless tools will only work with WEP not WPA

The first thing to do is to backup your network interfaces file.  Execute sudo mv /etc/network/interfaces /etc/network/interfaces~.

Then if you are not using ndiswrapper you should be able to remove these lines:
/sbin/modprobe ndiswrapper # load ndiswrapper 
sleep 1 # wait until ndiswrapper loaded.  

Also any instances of eth1 should be replaced with the interface name of your wireless device.  

I have included the working version of the scanWAP script.  I have also included the script makeprofile.  This script will generate a network interfaces file that scanWAP will link to /etc/network/interfaces.  interfaces is used by Debian based distros to control the network interfaces at boot up and when ifup and ifdown are used.  You will need to  create these directories:
/etc/network/profiles
/etc/network/test

profiles is where the interfaces files are kept and test is where the scripts used to set the wireless adapter to the settings for each WAP.

Place makeprofiles in /usr/bin so it will be in your path.  Execute sudo chmod +x /usr/bin/makeprofile to make the script executable.  You will need to run the makeprofile script for each WAP you connect to and want to test for during bootup.  Make sure you run it with sudo.  Like this sudo makeprofile.

Next you will need to place scanWAP in /etc/init.d and execute sudo chmod +x /etc/init.d/scanWAP to make this executable.  Then we need to make a link to a file in rcS.d to start the script during bootup before the network interfaces are brought up.  Execute sudo ln -s /etc/init.d/scanWAP /etc/rcS.d/S37scanWAP.

It should work now.  If you have any questions let me know.  Also anyone should feel free to use or modify these scripts anyway they wish.

filename /etc/init.d/scanWAP:

#! /bin/sh

declare -a networks     # array to hold profile names
declare n=0             # variable to hold counter
declare AP              # variable to hold MAC of AP

networks=(`/bin/ls /etc/network/test | cat`)    # populate array netwoks with profile names

/sbin/modprobe ndiswrapper # load ndiswrapper
sleep 1 # wait until ndiswrapper loaded

until test -z ${networks[n]}    # loop until networks returns a null
do
        /etc/network/test/${networks[n]}        # run iwconfig with settings for each network
        echo ${networks[n]}
        sleep 1 # sleep until wireless is set
        AP=`/sbin/iwconfig eth1 | grep Not-Associated -o`       # test if AP MAC is default meaning no connection
        if test -z $AP  # if variable AP is null we have a connection so set interfaces to link to correct profile and exit
        then
                /bin/rm -f /etc/network/interfaces
                /bin/ln -vs /etc/network/profiles/${networks[n]} /etc/network/interfaces
                exit 0
        fi
        let n+=1
done

/bin/ln -sv /etc/network/profiles/none /etc/network/interfaces # set profiles to none

filename /usr/bin/makeprofile:

#! /bin/sh

declare essid
declare key
declare network

echo " makeprofile: a script to create network profiles"

echo "What is the SSID:"
read essid

echo "What is the WEP key:"
read key

echo "What is the network name you wish use:"
read network

echo -e "#! /bin/bash\n\n/sbin/iwconfig eth1 essid $essid key $key commit" > /etc/network/test/$network

echo -e "# This file describes the network interfaces available on your system\n# and how to activate them. For more information, see interfaces(5).\n\n# The loopback network interface\nauto lo\niface lo inet loopback\n\n# The primary network interface\n\niface eth0 inet dhcp\n\niface eth1 inet dhcp\nwireless-essid $essid\nwireless-key $key\nauto eth1" > /etc/network/profiles/$network


filename /usr/network/profiles/none:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

iface eth1 inet dhcp

---

