---
title: "Network Manager doesn't"
date: 2006-06-01
forum: Desktop Environments
---

### Post by ubuntubrian on 2006-06-01
I'm continuing this from the Dapper development forum. 
I have NetworkManager daemon installed and on the menu bar. It just sits there with an exclamation point on it and when I click on it it shows a greyed out "wired network" and right clicking shows a checked "enable networking" and a greyed out "connection information". I also have the Network Status daemon running and I know  the difference between them. I currently use wifiradar but would like to get the native NetworkManager working.

---

### Post by NiN on 2006-06-01
have you commented out your network card settings in /etc/network/interfaces?

Network manager doesn't like them.

---

### Post by ubuntubrian on 2006-06-03
Here're the file contents. Would you be so good as to let me know which to comment out?
Thanks

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth1


iface eth1 inet dhcp
#wireless-essid SFBC
wireless-essid home
wireless-key 245EBEDA9A

---

### Post by atomic0x on 2006-06-03
[QUOTE=ubuntubrian]Here're the file contents. Would you be so good as to let me know which to comment out?
Thanks

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth1


iface eth1 inet dhcp
#wireless-essid SFBC
wireless-essid home
wireless-key 245EBEDA9A[/QUOTE]

I just finished fixing this on my machine.  Comment out everything after the loopback interface and it will work.  However, on my machine I had to manually start /usr/sbin/NetworkManager to get it to work.

---

### Post by ubuntubrian on 2006-06-04
Do you have to start it each time you reboot? If so I'll probably stick with wifiradar.

---

### Post by Antman on 2006-06-04
[QUOTE=atomic0x]I just finished fixing this on my machine.  Comment out everything after the loopback interface and it will work.  However, on my machine I had to manually start /usr/sbin/NetworkManager to get it to work.[/QUOTE]

Hey that trick worked great on my machine, thanks.

---

