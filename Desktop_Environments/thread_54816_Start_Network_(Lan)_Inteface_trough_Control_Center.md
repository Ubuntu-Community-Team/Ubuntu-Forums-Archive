---
title: "Start Network (Lan) Inteface trough Control Center"
date: 2005-08-06
forum: Desktop Environments
---

### Post by hans796 on 2005-08-06
Hi fellow Kubuntu users.. 

I'm running Kubuntu on an AMD 1.3 Ghz and 524 DDR Ram.
Overall im very impressed and the OS runs smothly.

I have two network cards:
1 is connected to internet
1 is for my LAN.

I can't start my Lan with KDE Contol center.
I click on "andministrator mode" and wright in the password, but then it stops responding..
I'm planning to use firestarter's "internet connection sharing" with my other PC running Windows XP. It has worked with "Ubuntu" and "Mandrake 2005 LE".
Any clues?

I can point out that I have done all upgrades: ap-get update, apt-get upgrade, apt-get dist-upgrade. 

I have KDE 3.4.2.

Thanks in advance and greetz from Sweden.  :grin:

---

### Post by hans796 on 2005-08-06
Fixed this problem, thanks do this thread:

[http://www.ubuntuforums.org/showthread.php?t=53700](http://www.ubuntuforums.org/showthread.php?t=53700)

Edited: /etc/network/interfaces

with these lines: 
auto eth1
iface eth1 inet static
address 192.68.0.1
netmask 255.255.255.0

That did it..

---

### Post by hans796 on 2005-08-06
Made som changes after looking closer at /etc/network/interfaces

Now it looks like this:
---------------------------------------------------------------------------------------------------

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
	map eth1

# The primary network interface
iface eth0 inet dhcp

# The secondary network interface
iface eth1 inet static
address 192.68.0.1
netmask 255.255.255.0

--------------------------------------------------------

i noticed that under "mapping hotplug" there was: map eth1, so i also wrote: map eth1
the under "# The secondary network interface" i deleted: auto eth1
i dont know the difference, but this also works, my second network card is autostarted

---

### Post by hans796 on 2005-08-06
[QUOTE=hans796]Made som changes after looking closer at /etc/network/interfaces

Now it looks like this:
---------------------------------------------------------------------------------------------------

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
	map eth1

# The primary network interface
iface eth0 inet dhcp

# The secondary network interface
iface eth1 inet static
address 192.68.0.1
netmask 255.255.255.0

--------------------------------------------------------

i noticed that under "mapping hotplug" there was: map eth1, so i also wrote: map eth1
the under "# The secondary network interface" i deleted: auto eth1
i dont know the difference, but this also works, my second network card is autostarted[/QUOTE]

Sorry network adress should of course be: 192.168.0.1

---

