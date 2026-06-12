---
title: "Does anybody have problems with wireless?"
date: 2005-03-21
forum: Desktop Environments
---

### Post by kubuntu_user on 2005-03-21
Hi,

I seems to be that i cannot make my wireless connection to work..
It doesn't get ip address. Yes, dhcp server is running and other clients running windows on my network get connected.

By the way, connection works fine in gnome

I was wondering if other people have experienced the same problem.

Thanks

---

### Post by knappen on 2005-03-22
Yes I had problems with my wireless network. I managed to connect but I only stay connected for about 15 - 30 minutes then it disconnects. After that I cannot reconnect.

---

### Post by lao_V on 2005-03-22
I'm assuming you're running KDE.

Have you configures your network via KDE wireless manager? What's in your /etc/network/interfaces file?

---

### Post by knappen on 2005-03-22
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
 script grep
 map eth0

# The primary network interface
iface eth0 inet dhcp
 # wireless-* options are implemented by the wireless-tools package
 wireless-mode managed
 wireless-essid any

It is a bit strange but when I try to enter the correct information in the Control Centre - Internet and Network - Wireless Network, KDE will not change to Administrator mode.

However, I can change the settings from the KWifimanager applet. 

Did I mention that this is the first time I ever used KDE?

---

### Post by techlord on 2005-03-22
I have a semi related question. When you update the kwifimanger information where is that data stored. I thought it would update my interfaces config but it does not. Also is there a way to modify your interfaces config file from inside of kde.

---

### Post by Darrena on 2005-03-22
I gave up on kwifimanager and used wifi radar instead (Yes I know it is a python-gtk app..)  Using that setup my connection easily!

---

### Post by Novack on 2005-03-23
I didn't manage to get the KWifi to connect to my AP at all. It got the signal but didn't connect even though I had the WEP key configured correctly.

I installed the Gnome System Tools and used it's network panel to configure the Wifi. It worked right away.

---

### Post by knappen on 2005-03-23
I just installed kubuntu over Warty. It worked better with Warty.

---

### Post by vvu on 2005-03-23
The only critical functionality NOT working in Kubuntu for me is the wireless!  I have the ndiswrapper set, wireless indicator (KWiFiManager) is good but no go...

I went and tried the fix for wireless config file - still no go.

What I did notice strange is that my eth0 has both IPv4 and IPv6 - but my wlan0 only has IPv6!  But the Network tools interface does NOT allow me to modify this (not a root issue but app feature).

Also, I have tried to (with iwconfig and ifconfig): down, set ssid, set channel, set mode, up  - STILL no go.  

I just hope that this critical feature for a GUI is enhanced in Linux primarily.  (When multiple people suggest multiple tools because one may work or one does not - that's not exactly robust - yeah great for choice, but I just need one to work to standardize on).

I hear debates with CLI people that we "don't" need no stinkin GUI - hello!  It's 2005!  Get with the program...if Linux will ever surpass Microsoft Windows - we have to make it "user friendly" - so get off the CLI high horse or being old school and think more of the general goal - Linux adoption! - OPTIONS.

Sorry for the rant, but I have figured out for myself, reading, and help of others here how to get around Linux pretty well for just couple of days (VPN to work, Exchange system setup, VMWare,m etc) - it is very annoying however, when you have old school mentality pertaining to these type of things - again - SPREAD Linux via "user friendliness" features.  Wheeewwww!

---

### Post by knappen on 2005-03-24
vvu - Cannot agree more. 

We all now that first impression lasts. Just have a look at the installation of a Linux system. In most cases it looks like you are installing something from the 1980s! That includes ubuntu. And it is difficult to change a persons first impression, and that is a fact.

And after that you have to tell the new user that he/she has to edit a config manually via a terminal window... There should be no reason to have a system administrator standing by just to do minor changes. I really enjoy working with computers but not all people do. (strange, I know) 

I love ubuntu and have been using it since september last year and would never go back to Windows.

---

### Post by NetworkNed on 2005-05-15
[QUOTE=Darrena]I gave up on kwifimanager and used wifi radar instead (Yes I know it is a python-gtk app..)  Using that setup my connection easily![/QUOTE]

Is there a package for this? I'm new to Ubuntu, but can't seem to find anything corresponding with either `dpkg -l "*wifi*"` or `apt-cache search radar`

---

### Post by crashedmind on 2005-07-18
After a few evenings  playing around I finally managed to get my wireless networking up and running.
My system is a dell inspiron 9100 XPS with Kubuntu OS.

I got stuck on the stage where I had installed Ndiswrapper and everything seemed ok - I even had a signal but my Access Point value was all zeros according to KWiFimanager and iwconfig.
So here's what I had to do from that point on to get my wireless working.
All command line stuff is shown prefixed with a $.

bring down all ifs then bring up wlan0
	$sudo ifconfig wlan0 down
	$sudo ifconfig eth0 down
	$sudo ifconfig wlan0 up

kwifimanager - scan for networks: no nw present
$sudo iwlist wlan0 scan
kwifimanager - scan for networks: nw present: 3Com - finds essid correctly
$sudo iwconfig wlan0 essid 3Com
kwifimanager - status indicates
	Access Point 00:0X:XX:XX:XX:XX
where X is non-zero.

The magic missing ingredients in all this were:
1, disconnect eth0 i.e. remove the cable from the NIC. Then reboot (a full reboot might not be necessary but it worked)
I came across this problem in othe posts.
2, $sudo iwlist wlan0 scan

The previously mentioned IPV6 for wireless is a red-herring I think - I also had this and investigated it but concluded this was not the issue.

I also have vmware running on my kubuntu host with a linux guest successfully communicating via the wireless NIC. According to a post I read Vmware 5 does not support bridging to a wireless NIC so I changed my Vmware guest machine to use NAT instead.

My /etc/network/interfaces file is below (note that it is not configured with security in mind - I wanted to get barebones up and working first)

Hope this helps.
Chris

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

#The ethernet network interface
auto eth0
iface eth0 inet dhcp


#The wireless network interface
auto wlan0
iface wlan0 inet dhcp    
	wireless_essid 3Com
	wirelss_mode managed
	wireless_nick kubuntu

---

