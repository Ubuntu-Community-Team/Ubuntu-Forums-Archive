---
title: "dhcp stopped working after installing kubuntu-desktop"
date: 2005-12-13
forum: General Help
---

### Post by Muqker on 2005-12-13
I couldn't connect to the Internet anymore after installing kubuntu-desktop, because dhcp sopped working. It worked fine before installing kubuntu-desktop. 

Issuing the command "ifconfig" did not show eth0 at all; running the command "dhclient eth0" failed to acquire an IP address, ending with the error message "No DHCPOFFERS Available". 

The _solution_ was to start kcontrol (with "sudo kcontrol" because the "Administrator Mode" button fails to work sometimes), go to "Internet & Network" -> "Network Settings", selected the interface on which I expected dhcp to automatically acquire an IP address (eth0 in my case), clicked "Configure Interface" and checked "Activate when the computer starts". The same result can be obtained appending the line "auto eth0" to the file "/etc/network/interfaces". After a reboot, all worked fine once again.

I'm posting this thinking it may be of help to others (as many google searches end up in the ubuntuforums.org site), and also hoping this problem will be fixed in future ubuntu releases.

---

