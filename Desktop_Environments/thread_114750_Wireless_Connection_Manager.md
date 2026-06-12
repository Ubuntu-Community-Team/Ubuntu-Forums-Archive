---
title: "Wireless Connection Manager"
date: 2006-01-09
forum: Desktop Environments
---

### Post by nocturn on 2006-01-09
I'm trying to get wireless roaming set up in a user friendly manner (for myself, I had som shell scripts to switch, but that is not for everyone).

So far I looked at every package I could find, but found them all lacking...

- NetworkManager
The nicest of any of them and worked well.  But with NM, my connection is down at boottime (only comes up after logging in).   I would like it to at least bring up the network when I'm on my own network.

- Netapplet
Works well, but only allows setting essid and key, so no different IP or DNS settings per network.  I would like to use a static IP at home and a dynamic one at other locations.

- gtkwifi
Works very well, brings up the interface at boot and all, but forces dhcp on which I don't want in my home network (static IP).

- wifi-radar
This one looked promising (supporting many of my requirements), but it does not work at all.  It scans for my networks and shows the available ones, but fails to connect (it says working, and stays there).

Are there any options left?

We are selling laptops with Ubuntu preinstalled and I would like to ship a good wireless applet with them by default as well as use it for my wife's laptop...

---

### Post by uberlaff on 2006-01-24
I would like get some more information on this myself.  I've used NetworkManager to try and make my wireless life a little easier and what I found was that it worked great as long as the wireless network didn't require a WEP Key.  When I tried to connect to a network that required a WEP Key it would pretty much time out on me and never make a connection.  This happened if I ran NetworkManager with Sudo or without.  

Anyone have any good expierence with one of these Wireless Connection Managers?  Being a person that is constantly moving around and switching connections I would love to have a good wireless manager.

---

### Post by stardotstar on 2006-01-25
I relate directly to almost all of this.  Having broken my entire system meddling with the wifi I did a complete reinstall and am back to the situations you both describe:

1) NM is the best for ease of use as long as you don't rely on WEP (seems to be ok at my work place with D-Link but hopeless at home with the Net-Gear - as nocturn says - it times out and  keeps asking for keys and only rarely the keyring password.  Once it has lost it it usually requires a reboot of both the notebook and the router.  Incidently, NM seems to be fine with no SSID broadcast and makes a good and reliable connection if there is no WEP. 

I am still a bit confused about the different ways of offering wep keys:

64 bit/Ascii/Hex 128bit etc...  I got the most reliable results at work with the router set to ask for a 64 bit hex key rather than a password (even though the password string generated the hex key...)

2) WiFi radar finds networks well but hangs indefinitely on "working" or "acquiring IP" for some reason so I have abandoned it.

I have not tried gtkwifi although it sounds good because I tend to rely on dhcp and because I am not having luck with wep at home have to secure my home router with mac address filtering (would prefer wep as well!)

---

### Post by scubajeff on 2006-01-26
I used to have the indefinitely on "working" or "acquiring IP" problem with wifi-radar, solved it by editing the configuration file "/etc/wifi-radar.conf" and change the
```

ifup_required = False

```

to 
```

ifup_required = True

```

---

### Post by stardotstar on 2006-01-26
I have been doing some syslog tracking and find that usually when Network Manager goes into a "won't connect to a network that has otherwise worked fine all day" mode it seems to be trying to connect and the dhcpd is getting an "[FONT=Arial][SIZE=4]APIPA".
[/SIZE][/FONT]

The log shows that after trying to negotiate a dhcp request with 192.168.0.1 it ends up assigning 169.254.131.165

Now this seems unacceptable to the NM and it terminates the connection (I Don't know if this is because it fails to get a default gateway or valid DNS or what - especially since the SSID responds with 192.168.0.1 - and therefore in the absence of routing would be unavailable!)

If I could get online with that box I could post the logs - very wierd.  I have tried rebooting the router and the box, also logging in and out etc...  Nothing seems to cure this at the moment - and I have turned the wep off at this stage!

I again wonder if there is some configuration of Network Manager we could tune - can't seem to find anything useful googling APIPA - seems it is exclusively a Windows thing for devices that do not have any other way of assigning a valid IP so they use the Automatic Private IP space to grab something to start with.  Could this be a feature that needs turning off on Network Manager or is it perhaps being pushed by the router??

Strange...

Thanks scubajeff that is worth trying next time I wrangle with wifi-radar!

---

### Post by bschuteker on 2006-02-02
So far I have not had any dropped connections but I also dont like the fact that it doesn't come up until login. It then asks for the keyring PW. Is this because I am using wep? If I disable wep will it ask for a password still? Is there a way to get it loaded during boot up?

---

### Post by stardotstar on 2006-02-04
Network Manager does not initialise during boot up - you can disable the standard network interfaces during bootup but I just hit ctrl-c because sometimes use the wired connection that comes up straight away.

If you turn off WEP you will not need the password or keyring manager but remember it is a combination of access controls that secure your network.  Hidden SSIDs can easily be detected, mac address filters can be spoofed and without wep other networks on the same channel can cause association problems.  

Don't know yet how to set up keyring with an effective authentication that supercedes using an encrypted home directory or pass protected keyring...

2c for what its worth

Will

---

