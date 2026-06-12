---
title: "Dell Latitude d620 Wireless issue"
date: 2011-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jenkinsboy on 2011-07-28
Hello

I just installed Ubuntu 11.04 on a Dell latitude D620
and for some reason its not able to Detect the wireless network,  i even installed and re installed the driver for it.

Ehthernet port works fine.
I was wondering if anyone had the same or similar issue.

I Visited this Website ([http://ubuntuforums.org/showthread.php?t=1749151](http://ubuntuforums.org/showthread.php?t=1749151))
I went into the terminal and typed (lsmod | grep b43)
and (dmesg | grep b43. 

One of the messages say (no IPv6 routers available).

---

### Post by bayouoldguy on 2011-07-28
I suggest you read up on most of this thread, try a few of the recommended fixes....see where it takes you.....:G:

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

My Last attempt: ( Running a Dell D620 w/Windows Vista Business , works fine thru Windows/Linksys E2000 & can "hardwire" to the internet on a USB/Ubuntu stick load).

i tried to access & set up Ubuntu 11.04 & my wireless net. was not able to "enter" any terminal commands changing the wireless setups. If I re-booted, I lost the settings in the USB stick.
Saw all the problems of others trying to get Wireless up & came to this conclusion:
I stopped trying to use the USB/Ubuntu 11.04 stick & went back and reloaded Ubuntu 10.04LTS. Was able to get up & running on Wireless after uninstalling "bcmwl-kernel-source" & "bcmwl-modaliases", then installing "b43-fwcutter", re-booting, configuring my Wireless SSID, Security as: WPA & WPA2 Personal & putting in the passcode. A re-boot started up the Wireless & showing ALL neighborhood nets !.
Therefore: I installed Ubuntu 10.04LTS on my Dell D620 until
the Ubuntu Team/users correct the Driver situation !..."G"

---

### Post by nm_geo on 2011-07-28
> **jenkinsboy said:**
> Hello

I just installed Ubuntu 11.04 on a Dell latitude D620
and for some reason its not able to Detect the wireless network,  i even installed and re installed the driver for it.

Ehthernet port works fine.
I was wondering if anyone had the same or similar issue.

I Visited this Website ([http://ubuntuforums.org/showthread.php?t=1749151](http://ubuntuforums.org/showthread.php?t=1749151))
I went into the terminal and typed (lsmod | grep b43)
and (dmesg | grep b43. 

One of the messages say (no IPv6 routers available).

I also have a D620.. I have a 320GB drive works like a champ.  Installed a little wasteful 4.0GB of RAM, and i try out lots of distros.

I have had Natty installed since the first alpha came out and have upgraded it to kernel 3.03 I believe, and I am presently testing the next version Oneiric.  I am not sure what wireless card you have but if you are installing drivers I assume it is a Broadcom.

If you like copy and paste this in terminal and paste results.

```
lspci -nn | grep 0280
```i assume that you are trying the STA (wl) driver typically in additional drivers.  If you have the chipset I think you have we can get it up and running well with the b43-fwcutter and firmware-b43-installer..

---

### Post by bayouoldguy on 2011-08-08
Re: Dell Latitude D600 Problem
Look what I found !....

[url]https://launchpad.net/ubuntu/maverick/i386/firmware-b43-installer
 & listed file:

firmware-b43-installer_4.150.10.5-4_all.deb (5.1 KiB)

I downloaded the file to the "Downloads" folder, & commanded to "extract".
It installed.....found my Wireless & is up & running from the USB stick !!.
I installed the b43-fwcutter package from the Synaptic Package manager first. The wireless apt always showed me "no firmware", & the "apt-get install firmware-b43-installer" command would not execute.

Now I guess I can upgrade to the 11.04 version !......"G"

All you guys having Dell D6XX series laptops with the Broadcom BCM4311
802.11 b/g Wlan wireless card may want to try this......
__________________

---

### Post by MARP1961 on 2011-08-12
Yes B43 works and STA (the only one offered by Additional Drivers in Natty) doesn't!

I think a pre-install of the STA driver is causing B43 to be blacklisted so I simply:

Did a fresh install of Natty, connected an ethernet cable (for updates and downloads), ignored the 'Additional Drivers' prompt to install drivers and then opened Synaptic Package Manager and searched for 'B43 fw cutter installer'. I then installed this, rebooted and unplugged the ethernet cable. By left clicking the Network Manager I found my router and edited it to accept ALL USERS.

Success! 

There seems to be an issue with Natty and the Broadcom drivers that wasn't the case in Lucid (which offers STA and B43). Why is this?

---

### Post by nm_geo on 2011-08-12
> **MARP1961 said:**
> Yes B43 works and STA (the only one offered by Additional Drivers in Natty) doesn't!
 
I think a pre-install of the STA driver is causing B43 to be blacklisted so I simply:
 
Did a fresh install of Natty, connected an ethernet cable (for updates and downloads), ignored the 'Additional Drivers' prompt to install drivers and then opened Synaptic Package Manager and searched for 'B43 fw cutter installer'. I then installed this, rebooted and unplugged the ethernet cable. By left clicking the Network Manager I found my router and edited it to accept ALL USERS.
 
Success! 
 
There seems to be an issue with Natty and the Broadcom drivers that wasn't the case in Lucid (which offers STA and B43). Why is this?
 
Progress..
 
The STA (wl) driver works for me in Maverick, but not in Natty or Oneiric (testing now)... The wireless drivers are being changed all the time and added to the newer kernels and sometimes they are buggy.
 
I try the STA (wl) on all my installs with my BCM4311 just to see if it will work (cause I am curious).  After I confirm it will not I deactivate it and get rid of the blacklists file and install the b43-fwcutter and firmware-b43-installer. That works for my chipset in 14e:4311..

---

### Post by goldstoned on 2011-08-12
Hi

I had a problem with a D600 also. It had an intel wifi card and wouldnt keep a constant connection until I tried the following after installing network manager from software centre

[COLOR=#000103][FONT=Arial]sudo apt-get
sudo apt-get install wpasupplicant
sudo apt-get install network-manager-gnome [COLOR=#3333ff][COLOR=#3333FF !important][FONT=inherit !important][COLOR=#3333FF !important][FONT=inherit !important]network[/FONT][/FONT][/COLOR][/FONT][/COLOR][FONT=Arial][/COLOR]-manager
sudo gedit /etc/network/interfaces
Comment out everything other than &#8220;lo&#8221; entries in that file and save the file
Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
sudo touch /etc/default/wpasupplicant
Reboot your system or use the following command
sudo /etc/init.d/dbus restart

Then it worked. 

[/FONT][/COLOR]

---

