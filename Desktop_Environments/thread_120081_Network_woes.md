---
title: "Network woes"
date: 2006-01-20
forum: Desktop Environments
---

### Post by pressman157 on 2006-01-20
Hi all. I'm new to (K)Ubuntu, and I'm having some problems with my Internet connection. Other than this one problem I really like Kubuntu. Y'all done good.

Hardware: One plain-jane PC wired to a Linksys BefSR41 plain-jane router hooked to a cable modem. The connection is shared with two Macs.

What I've tried:

1) Searched and searched the archives. I found a couple of methods to
use the Network Settings control panel after it ceases to function. One method involves logging in as root (that can't be good) The other method is to open kcontrol in an xterm, so at least I can use the GUI to configure the network. I really couldn't find anything else that specifically addressed my tale of woe.

2) Configured the network manually using the same settings that worked with Mandrake. No go.

3)Set up the router and both macs to use DHCP. No go. I re-installed and used the DHCP option. The installer reported a networking success. Still no go.

4)Manually entered the DNS server and names servers into NetworkSettings (using DHCP). The connection comes up, but is dropped at random and after a reboot.

5) Re-set the router before each connection attempt.

Thanks for looking. I like Kubuntu and I really don't want to give up on it, so any hints would be appreciated.

---

### Post by darth_vector on 2006-01-20
can you post the output of```
cat /etc/network/interfaces
cat /etc/resolv.conf
```

are the macs having connection problems at all? do you have any reason to suspect a problem with the network card on the Kubuntu machine?

---

### Post by pressman157 on 2006-01-20
yessir:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0


/etc/resolv.conf:

nameserver 68.6.16.30
nameserver 68.6.16.25
domain sd.cox.net

---

### Post by pressman157 on 2006-01-20
Both Macs are connecting fine. The network card was working three days ago with Mandrake 10.1.

Thanks for the reply

---

### Post by darth_vector on 2006-01-20
if the dhcp is not working, you should try to set up the connection manually. to do this you will have to edit /etc/network/interfaces as root```
sudo gedit /etc/network/interfaces
```get rid of the line```
iface eth0 inet dhcp
```and replace it with something like```
iface eth0 inet static
address <an ip address in the same subnet as your router>
netmask <probably 255.255.255.0>
gateway <the ip address of your router>
```

to enable these new preferences type```
sudo /etc/init.d/network restart
```and let us know how you go.

EDIT: was mandrake or any of the macs using DHCP by the way? it may be something silly, like your DHCP range only fitting two computers.

---

### Post by pressman157 on 2006-01-20
I did as you suggested, edited /etc/network/ and restarted the network without success. I changed the router settings as well.

I then edited /etc/resolv.conf and plugged in the dns adresses. After a reboot the network is still up, so I'm optimistic. It still doesn't connect with the timeserver at boot, however.

Thank you very much for pointing me in the right direction

Greg Richardson

---

### Post by stream303 on 2006-01-21
> 
4)Manually entered the DNS server and names servers into NetworkSettings (using DHCP). The connection comes up, but is dropped at random and after a reboot.

No sweat.  Since you know what your nameservers really are, edit
**/etc/dhcp3/dhclient.conf **  (sudo gedit /etc/dhcp3/dhclient.conf)

and add this just before the "request" line:  (with your real nameservers of course)
[B]
prepend domain-name-servers 123.45.67.89, 123.45.67.90;[/B]

Just separate multiple entries with a comma and don't forget the semicolon at the end.

Now bring your interface down and up again (more elegant than rebooting)
sudo ifdown eth0
sudo ifup eth0

This will force dns entries into your /etc/resolv.conf file so you don't have to manually edit this file, or go into network settings after each reboot.

---

