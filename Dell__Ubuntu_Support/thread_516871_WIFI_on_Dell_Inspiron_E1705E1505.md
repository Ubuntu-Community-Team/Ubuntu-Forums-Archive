---
title: "WIFI on Dell Inspiron E1705/E1505"
date: 2007-08-03
forum: Dell  Ubuntu Support
---

### Post by dynamorx1 on 2007-08-03
I found this while looking for info on how to get my WIFI working on my Dell Laptop. I figured that would not be the only one needing this info so here it is I hope that it helps some one. 
Reffrence: [http://forums.techguy.org/networking/581301-solved-problem-dell-1390-wireless.html](http://forums.techguy.org/networking/581301-solved-problem-dell-1390-wireless.html)

HOWTO: Dell Inspiron Wireless (Broadcom 1390 WLAN)
This HOWTO describes how to get Wifi working on your Dell Inspiron E1505/6400 laptop using Ndiswrapper. This applies if you have the Broadcom "Dell Wireless 1390 WLAN MiniCard", which as far as I know, is the cheaper, low-end version that Dell currently offers in this laptop. This HOWTO has been tested and works with both 32 bit and 64 bit ubuntu, and uses the exact same method for both.

This HOWTO supports:

* Feisty Fawn 7.04
* Edgy Eft 6.10
* Dapper Drake 6.06




STEP 1: CLEAN YOUR SYSTEM

IMPORTANT NOTE ABOUT CLEANING YOUR SYSTEM:

One of the most common reasons that many people can't get their wireless working is because their system is in a state of chaos. If you have made ANY previous attempts to get your wireless working -- either using fwcutter, ndiswrapper, or the bcm43xx drivers -- this how-to will most likely not work UNTIL you reverse your previous changes. In many cases, it is much easier to simply reinstall ubuntu and come straight to this how-to. Alternatively, you can manually clean your system of the previous attempts, as outlined in various posts throughout this thread. But BE WARNED: If you have done ANY previous work on your wireless, there is almost no chance that this how-to will work unless you clean your system.

If you have a fresh install of Ubuntu, you need to remove any and all versions of Ndiswrapper that come installed by default on your system:

Code:

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils

Don't worry if you get errors about not being able to find or remove these -- we're just making sure they're not present before we get started.



STEP 2: GET NEEDED PACKAGES

We'll need to install compiling tools (don't panic when you read that, just bear with me), the latest kernel headers, and then the source code for the latest ndiswrapper (seriously, don't panic. This will be very simple), and the wireless drivers from Dell.com.

Code:

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)

NOTE: The characters around `uname -r` are BACK TICS, NOT apostrophes. A back tic is usually located at the top left of your keyboard, to the left of the 1 key. The command WILL NOT WORK if you use apostrophes. Just copy/paste the commands from this how-to in to your terminal to avoid making typos.

At this point, you need to go to the ndiswrapper sourceforge site and get the latest version of the Ndiswrapper program. As of 1 April 2007, the latest version is 1.41:

Code:

wget [http://internap.dl.sourceforge.net/s...er-1.41.tar.gz](http://internap.dl.sourceforge.net/s...er-1.41.tar.gz)

If that wget doesn't work, just go here: [http://sourceforge.net/project/showf...group_id=93482](http://sourceforge.net/project/showf...group_id=93482)

Uncompress the ndiswrapper source (in my example, the file name is ndiswrapper-1.41.tar.gz):

Code:

tar -xzvf ndiswrapper-1.41.tar.gz

Finally, we need to blacklist the broken and useless bcm43xx firmware drivers that try to load in a default ubuntu install:

Code:

sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist

NOTE: If the above command gives you a permission denied error, try this code instead:

Code:

sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit

YOU MUST REBOOT NOW!



STEP 3: COMPILE PROGRAM

Now we'll complile the Ndiswrapper program. In a terminal, go to the directory where you extracted ndiswrapper and execute the following:

Code:

sudo make uninstall

IMPORTANT: Do the above command multiple times. You can stop when you get the message that says something about no files or directories found.

Code:

sudo make
sudo make install



STEP 4: INSTALL DRIVERS

If that worked, then you now have Ndiswrapper installed. Now we need to install the drivers. In a terminal, go to the directory where you have the R151517.EXE file:

Code:

unzip -a R151517.EXE

Now change directories (cd) to the DRIVER directory that was just extracted.

Code:

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

you should see a message that says driver present, hardware detected

Code:

sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules

Some users have reported the need to reboot here.



STEP 5: TEST WIRELESS

Your wifi light on your laptop should be illuminated, and you're all set! Try running this to see if your wireless card is functioning properly:

Code:

sudo iwlist scanning

Even if it doesn't detect any wireless networks in range, it will still tell you if linux is recognizing your wireless card properly. If you'd like a better way to scan for wireless networks, I'd suggest installing/using network-manager or wifi-radar.


TO ALL WHO REQUEST HELP:

1) Please indicate:

1. your laptop model
2. ubuntu version
3. your lspci output
4. the relevant rows from /var/log/syslog
5. the relevant rows from dmesg
6. any unexpected output when following the steps in the how-to


2) If your wireless card is being recognized by the system, but you simply cannot connect to your desired wireless network, please understand that your issue is beyond the scope of this how-to, due largely to the fact that such issues are very complicated and often have absolutely nothing to do with the way you got ubuntu to recognize your wireless card. That said, I will do what I can to help. My first suggestion will always be to turn off all encryption first to see if you can at least connect to an open network.

NOTES:

- Dell driver version updated to R151517.EXE on 30 March 2007
- Ndiswrapper version updated to 1.41 on 1 April 2007
- If you are using a Dell laptop that's NOT model E1505, you need to go to Dell.com and search for the drivers that correspond to your specific model. Use those instead.

---

### Post by leo_rockway on 2007-08-03
i have a dell inspiron e1705 and i didnt use ndiswrapper. instead, i followed this guide to use the native drivers.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

you basically type this in

> sudo apt-get install bcm43xx-fwcutter
sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` <downloaded file>
sudo modprobe bcm43xx

where <downloaded file> is [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o)

it is way easier than using the windoze drivers and it worked for me.

---

### Post by shaul on 2007-08-04
just got it working!!!! great how-to :)
thanks.

dell inspiron e1705.

---

### Post by franny on 2007-08-14
My son got my wifi working but when I turn on my computer there is not a simple connect option. It will allow me to go into a manual configuration which I know better and will not touch and eventually it ends up connected. But why is there no simple option allowing me to connect now?

---

### Post by dvader on 2007-09-01
Will the above How To work with my laptop  ???

 Dell Inspiron 1501  AMD 64 athlon , dell wireless 1390 ... 802.11g 

Ubuntu 7.04 Fiesty , dual boot with XP 


And what files do I need ????  havent  made ay changes in the wifi mode , a plain install .. Using a wired net connection 

Thanks   Dvader

---

