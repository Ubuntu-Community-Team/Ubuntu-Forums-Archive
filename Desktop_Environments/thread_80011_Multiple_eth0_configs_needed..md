---
title: "Multiple eth0 configs needed."
date: 2005-10-21
forum: Desktop Environments
---

### Post by Armagguedes on 2005-10-21
[SIZE=2]Good afternoon. I generally access the intarnets in two places: home and college, both cabled access (i still haven tried to use my wifi, because i need to configure WPA). 

Now, i just managed to connect to the college intranet, but it took me quite a while, because after booting when i '[SIZE=1]sudo kcontrol[/SIZE]'ed (because the "[SIZE=1]Administrator mode[/SIZE]" button is broken: KDE bug, i know), the [SIZE=1]eth0[/SIZE] was disabled and when i tried to enable it, it disabled itself immediatly ([SIZE=1]eth1[/SIZE] too, but i'm not worried about that one for the moment). Any ideas why?

After i deleted some stuff out of [SIZE=1]/etc/network/interfaces[/SIZE] it started working. This is my current [SIZE=1]interfaces[/SIZE], with the 2 initial comments ommited:

[/SIZE][INDENT]# The loopback network interface
  
auto lo
iface lo inet loopback
  
  
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
  
# The primary network interface
iface eth0 inet static
     hostname 193.136.0.0
    address 193.136.140.219
    netmask 255.255.255.0
    gateway 193.136.140.254
    dns 193.136.128.1 193.136.128.2
  
auto eth0
  
iface eth1 inet dhcp
  
[/INDENT][SIZE=2]Now this is what i need, one way or the other, to access the univ's intranet. However, at home, my Linksys WAG54G has DHCP on. I could add a commented line with "[SIZE=1]iface eth0 inet dhcp[/SIZE]", but that would require me to edit the file every time i changed networks and mass-(un)comment (and possibily rebooting: i believe there is another way?).

I read on [SIZE=1]networks[SIZE=2]' [SIZE=1]manpages[SIZE=2] that you can use a script that maps several combinations (eth0-home, eth0-univ, etc), but i can't script. Any other way, or any available pre-made scripts out there?[/SIZE][/SIZE][/SIZE][/SIZE]

Is "[SIZE=1]auto eth0[/SIZE]" supposed to be above "[/SIZE]iface eth0 inet static[SIZE=2]"? And[/SIZE][SIZE=2] isn't "[SIZE=1]auto lo[/SIZE]" supposed to have as arguments (?) the [SIZE=1]eth#[SIZE=2] devices? And, out of mere curiosity, what does[/SIZE][/SIZE][/SIZE][SIZE=2] "[SIZE=1]lo[/SIZE]" stand for?

Thanks for your help.
Cheers.

[/SIZE]

---

### Post by hvbakel on 2005-10-21
you might try the laptop-netconf package, which allows you to automatically setup your network parameters depending on the network you're connecting to. You will have to edit a few configuration files (in /etc/laptop-netconf/), but it's relatively straightforward.

---

