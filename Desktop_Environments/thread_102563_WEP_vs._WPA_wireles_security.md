---
title: "WEP vs. WPA wireles security"
date: 2005-12-12
forum: Desktop Environments
---

### Post by arwin on 2005-12-12
I am a relative noobie to Ubuntu.  So far I like it, but sharing folders between a Ubuntu machine and a WinXP Pro machine has been challenging.  After reading how tos and many entries on this forum I finally managed to make my set up work.  The key was changing my network security from WPA to WEP Then everything worked as it should on the Gnome interface and the WinXP machines.  Based on my experience I advise using WEP if you are sharing a network with WinXP machines.  Oh yeah, for file sharing on Ubuntu I'm using Samba. I didn't need to make changes to smb.conf between WPA and switching to WEP

However, I'd like to know if this problem is unique to my setup or if there is a problem with wpasupplicant.  Also I wonder if the issue is with the madwifi driver shipped with Breezy conflicting with WPA.  I didn't up date madwifi driver.

With WPA security:
I could mount shared directories of both an XP Pro PC and XP home lappy on Ubuntu, but couldn't see either WinXP machine in Places in Gnome.  For the most part I used the GUI to configure Ubuntu (with the exception of WPA.)  Also I could see the Ubuntu machine from WinXP, but couldn't find the shared Ubuntu directories in either XP machine using network places.

Further, I could always ping the network, WinXP machines, and external sites from Ubuntu, but pinging the Ubuntu machine from either WinXP machine was not reliable (when the ping form XP worked it was fine, but the ping wasn't always answered.) This makes me suspect the madwifi driver.

I am using a TrendNET TEW-443PI wireless NIC.  This card uses an Atheros AR5212 chipset.

Here is a copy of my wpa_supplicant.conf file:
[HTML]<textarea rows="10" cols="50">
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="network_name"
        #psk="passkey"
        psk=hex_generated_by_wpa_passphrase
}
</textarea>[/HTML]

Here is a copy of my wpasupplicant file:
[HTML]<textarea rows="10" cols="50">
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless drive, typically optional.
#  -i <ifname>		Interface
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.
# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf -w"
</textarea>[/HTML]

Let me know if there are other statements that could be added to make WPA work with my setup.

---

### Post by firecat53 on 2005-12-12
Hey...can't say I've got any pearls of wisdom based on the info you gave, but I do have a happily networked home with 3 XP home and 2 linux machines (2 desktop, 2 laptop and 1 server) and I'm happily sharing and backing up as required between the machines. My wireless uses WPA, and it doesn't cause any issues at all with the networking. The following is my wireless setup on my Ubuntu laptop. There's a few minor differences from yours. I can also show you my samba config on the server and ubuntu laptop if you need it.  I compiled the madwifi (older version, not the newest ng...that's a project for another time!) drivers and wpa_supplicant from source.
Good luck!

Scott
```

# /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

#auto eth0

auto ath0
iface ath0 inet static
address 192.168.0.110
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid athome
pre-up /usr/local/sbin/wpa_supplicant -wB -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -p wpa_supplicant

# /etc/wpa_supplicant.conf
network={
   ssid="firecat4153"
   #psk="mypassphrase"
   psk=34150987asdfasdfjkh3407etcetcetc
   key_mgmt=WPA-PSK
   proto=WPA
}


# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless drive, typically optional.
#  -i <ifname>          Interface
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"

```

---

### Post by arwin on 2005-12-15
Thanks for the reply.  I tried to make my settings look more like yours.  I ran into problems (I think) with this line in your interfaces file:
```
pre-up /usr/local/sbin/wpa_supplicant -wB -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -p wpa_supplicant
```

I don't have wpa_supplicant in /usr/local/sbin.  If you have a chance could you tell me what this line is doing?  Thanks.

The other difference is I'm trying to use DHCP instead of a static IP.  I did see others on this forum who were able to make things work with static IPs.  It almost seems when I use WPA security I end up with half a connection.  I can ping other boxes, but they can't (reliably) ping me.  I also can connect to the web with Firefox.  Wierd.  I'm begining to think there is some sort of timing issue with assigning the IP from the router, but I'm really not sure.

I also tried to update madwifi.  I'm such a newbie I couldn't get this done either... although I think it may be because my build environment doesn't have the kernel-header package set up.

I think I'm going to have to dig into the manual so I understand what's going on instead of cutting and pasting commands and lines into files and hoping for the best.  Don't you just hate it when that happens ;) 

Of course it is tough to get motivated when it all works well with WEP security and that is probably good enough for my network.  I probably should do something more worthwhile like getting the shared printer on my WinXP box working :D 

Thanks again for the help.

---

### Post by firecat53 on 2005-12-15
My wpa_supplicant is located in a different place because I compiled it from scratch. I think (not positive) the default location is /usr/sbin. All you have to do is determine the path for it (type : "which wpa_supplicant") and insert that into the interfaces file. The pre-up command I believe just instructs that wpa_supplicant be started before the rest of the network startup commands are given to avoid any conflicts. Then post-down makes sure it's killed before the interfaces are brought up again. I've inadvertently had two or three instances of wpa_supplicant running at once before I got this all figured out, which wasn't helpful for having things work correctly!! The interface should automatically come up, including wpa_supplicant, when you start the computer or wake it up from suspend, and it should shut down automatically when you shutdown or suspend. If you messing around with things, "sudo ifup ath0" and "sudo ifdown ath0" should bring the interface, including wpa, cleanly up and down. Do a "ps -e" if you're having troubles to make sure you only have one instance of dhclient and/or wpa_supplicant running. I'm not positive, but you may have to add a killall dhclient somewhere to prevent multiple instances. Sorry I can't help more with that as I use static IP on my laptop.

Try setting up the static IP scenario instead of using dhcp. I thought that one of the issues with Madwifi and WPA was dhcp not working properly. But fixing that problem was many many problems ago......

Search for some of my other posts...I think I've described how to build Madwifi from source in a couple other places. Make sure you switch to gcc-3.4!

Good luck!

Scott

---

### Post by arwin on 2005-12-15
Thanks Scott,

I'll keep plunking away at it until I figure it out.   I appreciate your help and patience.

Arwin

---

