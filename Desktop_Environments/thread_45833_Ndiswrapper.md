---
title: "Ndiswrapper"
date: 2005-07-01
forum: Desktop Environments
---

### Post by improverrr on 2005-07-01
I am trying to get wireless up and running on my Kubuntu Laptop.  I can get it to work but not at boot up.  Anyone have any insight to why?  This is what I have done:

-- NDISWRAPPER INSTALLED
-- loaded the bcmw15 drivers, it came up about forcing the RadioState, so looking at another post, i changed the RadioState values to 0 in all of the config files in /etc/ndiswrapper

then in the console as root:

$ modprobe ndiswrapper (lights came on)
$ iwconfig wlan0 mode Managed
$ iwconfig wlan0 key restricted s:<KEY>
$ iwconfig wlan0 essid <ESSID NAME>
$ ifconfig wlan0 up
$ dhclient wlan0
-- FOUND DHCP - internet works
S ndiswrapper -m

but when I reboot, it doesnt come up, any ideas?

thanks!

---

### Post by MetalMusicAddict on 2005-07-01
Make sure your wlan0 is the default in your network config. Also look at /etc/network/interfaces to make sure the config is right. I had to edit mine. ;)

Look at [THIS](http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=40)   thread for all the info you should need.

---

### Post by improverrr on 2005-07-01
Thanks,

for starter, this is what I have done after reading your message:

--  got wlan0 working as listed in my first post
--  Kcontrol ->internet & networking -> network settings _wlan0 and made it open at boot
--  This still didnt work at boot

 I think my /etc/network/interfaces may need editing but I am not for sure what goes into it.  Would i basicaaly do the command listed in my fist post?


Thanks!

---

### Post by MetalMusicAddict on 2005-07-01
I had to do this to the interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0 **<-**change to **wlan0**

 # The primary network interface**<- Move this down**
iface eth0 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1


**TO HERE!!**
iface wlan0 inet static
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid wireless
wireless-key 8A2371746E85105B85050E80C4

auto wlan0 **<-Make sure that says wlan0**
```

---

### Post by improverrr on 2005-07-01
still not booting, but can always get online running the modprobe script listed in original post.

it is failing on bootup.  it is like the ndiswrapper isnt running.... listed below is the script you said to run.

/etc/network/interfaces
auto lo
iface lo inet loopback
mapping hotplug
 script grep
 map wlan0
auto wlan0
iface wlan0 inet dhcp
gateway 155.xx.xx.1
wireless-key s:<string key>
wireless-essid <essid name>

iface eth0 inet


any other ideas?

thanks!

---

### Post by MetalMusicAddict on 2005-07-02
I think your missing me. In a terminal type **sudo gedit /etc/network/interfaces**.
Then make sure the config that comes up looks something like mine posted above.

---

### Post by improverrr on 2005-07-02
[QUOTE=MetalMusicAddict]I think your missing me. In a terminal type **sudo gedit /etc/network/interfaces**.
Then make sure the config that comes up looks something like mine posted above.[/QUOTE]


yes.  Mine has all the info yours has except for address and netmask.  I shouldnt need those, mine is dhcp, not static.  If you look at mine, i just took out all of the comments, same info.

during Boot, i get the following errors:

pnp Evaluate _CVS
pnp fail to activate device 00:09

Now a big question for you or anyone else... when I type the iwconfig commands in manually (as in first post) where is this info going?  Because it is obviously working when I do that.  Is it possible to make a script to autmatically run this?

It shouldnt be this hard, I can get his working in 5 mins in mandrake.

thanks!

---

### Post by improverrr on 2005-07-02
ok, after a reinstall... I finally got it working.... one minor step was left off that isnt mentioned anywhere... so here is a nice HOW-TO of what I did:

ok I just installed kubuntu on my toshiba 2455 laptop & trying to get the wireless up and running.

Here is the exact steps I have done:

ok I just installed kubuntu on my toshiba 2455 laptop & trying to get the wireless up and running.

Here is the exact steps I have done to get wireless working:

-- installed ndiswrapper from disk
-- installed the drivers - when I did this it said something about the radiostate 1, so reading some other posts, I manually went into the conf files and changed the values to 0.
-- kcontrol ->internet & network -> network setting (no wlan0 listed)
-- konsole as root:
-- $ modprobe ndiswrapper (lights came on)
-- $ iwconfig wlan0 mode Managed
-- $ iwconfig wlan0 restricted key s: <string key>
-- $ iwconfig wlan0 essid <id name>
-- $ ifconfig wlan0 up
-- $ dhclient wlan0
BOOM gets a IP through DHCP, internet works well!
-- $ ndiswrapper -m

-- back kcontrol ->internet & network -> network setting wlan0 listed - configure it to start at boot.

-- kcontrol ->internet & network -> Wireless Network --->setup conf 1 with all information

-- edited /etc/network/interfaces to the following: (comments not added)
auto lo
iface lo inet loopback
script grep
map wlan0
iface wlan0 inet dhcp
wireless_mode Managed
wireless_key s: <string key>
wireless_essid <id name>
iface eth0 inet dhcp


NOW FOR THE ALL IMPORTANT STEP:

add NDISWRAPPER to the list in /etc/modules

WALLLAH!  It now boots

---

