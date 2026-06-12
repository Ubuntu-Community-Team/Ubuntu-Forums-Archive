---
title: "Auto Wireless"
date: 2005-11-17
forum: Desktop Environments
---

### Post by seismicmike on 2005-11-17
I consistently go back and forth between two wireless networks. One at school, the other at home.

I have both configurations in my /etc/network/interfaces

however, each time I boot up, I have to go in and comment out the one I don't want, uncomment the one I do want, and then reboot...

At school it looks like this:

```

#iface wlan0
#wireless-essid <homewireless>
#wireless-key <homekey>

iface wlan0
wireless-essid <schoolwireless>

```

so, when I go home, I have to change it to:
```

iface wlan0
wireless-essid <homewireless>
wireless-key <homekey>

#iface wlan0
#wireless-essid <schoolwireless>

```

and when I go back to school I have to change it back...

I tried just putting both of them in there together like this:

```

iface wlan0
wireless-essid <homewireless>
wireless-key <homekey>

iface wlan0
wireless-essid <schoolwireless>

```

and it worked (found the one it wanted and configured it), except that it deleted the one it didn't want from the interfaces file all toegether...

is there any way I can put both of them in there and have ubuntu configure the one it wants automatically without deleting the other???

---

### Post by 23meg on 2005-11-17
If you're using Gnome you may find [GTKWifi]("http://ubuntuforums.org/forumdisplay.php?f=74") useful.

---

### Post by KingBahamut on 2005-11-17
[http://ubuntuforums.org/showthread.php?t=91439](http://ubuntuforums.org/showthread.php?t=91439)

Hope this helps.

---

### Post by matthewv on 2005-11-17
[QUOTE=23meg]If you're using Gnome you may find [GTKWifi]("http://ubuntuforums.org/forumdisplay.php?f=74") useful.[/QUOTE]
or Network Manager (sudo apt-get install network-manager)

---

### Post by PokerFacePenguin on 2005-11-17
[QUOTE=seismicmike]and it worked (found the one it wanted and configured it), except that it deleted the one it didn't want from the interfaces file all toegether...

is there any way I can put both of them in there and have ubuntu configure the one it wants automatically without deleting the other???[/QUOTE]


why not have a permanent location for the file as a "backup" and write a startup script to copy that file at boot to the location it needs to be......then who cares if it got deleted altogether.   

Advanced Bash Scripting Guide found here:
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

### Post by seismicmike on 2005-11-18
well, network manager most definately didn't work right, so i'll have to try the script thing

---

### Post by seismicmike on 2005-11-22
Ok, here's what's up (summary and update):

At home my interfaces file looks like this:
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
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid 2WIRE794
wireless-key xxxxxxxxxx

#iface wlan0 inet dhcp
#wireless-essid cedarwireless

auto wlan0
```

At school it looks like this:
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
	map eth0

# The primary network interface
iface eth0 inet dhcp

#iface wlan0 inet dhcp
#wireless-essid 2WIRE794
#wireless-key xxxxxxxxxx

iface wlan0 inet dhcp
wireless-essid cedarwireless

auto wlan0
```

At home I tried putting it in as this:
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
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid 2WIRE794
wireless-key 8319089671

iface wlan0 inet dhcp
wireless-essid cedarwireless

auto wlan0
```

and it came back like this:
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
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid 2WIRE794
wireless-key 8319089671

auto wlan0
```

so I came on here and asked for help...

Well... I tried writing a script...

First I did
```
sudo cp /etc/network/interfaces ~/interfaces_backup
```
Then I wrote this script:
```
#!/bin/bash
# Wireless Setup

# Copies the backed up interfaces file from ~/ to /etc/network/
# Run as Root!

cp interfaces_backup /etc/network/interfaces

exit 0
```

The script works - it replaces the interfaces file in /etc/network with the backup file...

problems:

1) I don't know how to make the script run on boot
2) I use eth0 at work, and I found out that, at work, if I put the interfaces in with none of them commented out (see the third code block above) then it doesn't configure the eth0.

So, how do I fix these? How do I get it to figure out if I've got an eth0 or a wlan0 and configure accordingly? How do I run the script on startup?

Thank you for all your help :)

---

### Post by cdsboy on 2005-11-22
i believe you should be able to get it to start at boot if you put it here
> /etc/rc2.d/
and name it
> S20<filename>

---

### Post by piggyaugu on 2005-11-22
**netapplet**

that's exactly what you want.

It works with breezy. I am actually using it.

Maybe, it is not be in the default Breezy repo.

I cannot recall in which repo i found it.

U'd better do some searching.

---

### Post by seismicmike on 2005-11-30
how do you use netapplet... i just apt-getted it...

where is it?

---

