---
title: "Persistent network settings"
date: 2005-07-18
forum: Desktop Environments
---

### Post by mojo_risin on 2005-07-18
Hi,

I installed kubuntu 5.04 without an internet connection at the time so I skipped the configuration during install.
Now, each time I boot I have to go to control center network settings and enable my ethernet network device (eth1) and then do a "dhclient eth1".
How can I do this at startup? In kontrol center the "Activate when computer starts" option it's not remembered through diferent boots.

Thanks in advance.

---

### Post by mad_scientist03 on 2005-07-18
Try the update-rc.d command. I am a Fedora guy who has just recently started to try Ubuntu, so my familiarity is much more with chkconfig. It looks like update-rc.d is Ubuntu's equivalent for chkconfig.

---

### Post by skyboy on 2005-07-19
edit your /etc/network/interface

so it look like that :

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
        #wireless-* options are implemented by the wireless-tools package
        wireless-mode managed   #(if you have wireless)
        wireless-essid any

---

### Post by mojo_risin on 2005-07-19
It's better :) 
Now all I have to do is "dhclient eth1".

eth0 is my wireless interface and eth1 is my network card interface that is actually giving me an internet connection. 
"/etc/network/interfaces" looks like this now:
> # The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth1 inet dhcp

#iface eth0 inet

#wireless-* options are implemented by the wireless-tools package
wireless-mode managed #(if you have wireless)
wireless-essid any 

What can I do to avoid "dhclient eth1" manually?

---

### Post by skyboy on 2005-07-19
replace "map eth0"  with "map eth1"

and #comment the wireless extention you don't use
so you should ave something like :
 # The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
#map eth0
map eth1

iface eth1 inet dhcp

#iface eth0 inet

#wireless-* options are implemented by the wireless-tools package
#wireless-mode managed #(if you have wireless)
#wireless-essid any

---

### Post by mojo_risin on 2005-07-19
Thanks a lot! It worked.

Just one more question; can I easily switch from my netcard card to a wireless connection and vice-versa? That would be very cool as I have a laptop and soon I'll try a wireless connection.

---

### Post by skyboy on 2005-07-20
Yes you can, I have 2 wifi cards + lan card

Just edit the /etc/network/interface file according to your need.

Glad it's working for you now.
Problem Solved :)

---

