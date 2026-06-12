---
title: "network setup problem (NAT based ISP)"
date: 2005-08-16
forum: Desktop Environments
---

### Post by FCnix on 2005-08-16
hello i can't seem to get Konqueror to load www pages; in windows, my network settings are:
[list][*]IP address: 10.0.0.131
[*]Subnet mask: 255.255.255.0
[*]Default gateway: 10.0.0.1
[*]Preferred DNS server: 10.0.0.1[/list]
when i was installing Kubuntu, i typed in my IP address and few other network numbers and it seemed like Kubuntu was downloading some updates from internet during the installation, but when i tried to browse the web with Konqueror, it didn't work.

so i messed around with the network settings, read the help file but got no help.. i even emptied the whole 3rd tab in KDE network settings window from those settings starting with "IP6" etc but still nothing... so i searched the forums here, and tried *sudo ifup eth0* but it said my network is already configured:?

---

### Post by stevea1210 on 2005-08-16
Can you ping your gateway  (ping 10.0.0.1)?
if yes, can you ping gogle.com ?
if no can you ping 216.239.39.99 (gogles ip address)?

If your answers were yes, no, yes, then you have a dns issue.  That would be the first place I would look if it shows your network as up.  Please try that and let us know if it works.

---

### Post by FCnix on 2005-08-16
so i booted back to Kubuntu but since i left all the settings messed up, i can't ping anything since default gateway is not set, so i try to edit the network settings again, but i got this new problem now...

all the settings are greyed out like normal, but when i enter the administrator password, it does nothing - all the stuff still stays greyed out :?

also it kinda crashes every other time i enter the root password for network settings :mad:

also the Alt+F2 & *kdesu knetworkconf* command found in the help file says that knetworkconf was not found or sth ](*,)

---

### Post by stevea1210 on 2005-08-16
Try launching it from th shell using sudo kcontrol.  You should be able to edit the settings that way.  I personally had issues setting network information through the gui.  I did it in the shell.  I use DHCP and I don't rememer what command to use in order to add the gateway.  Sorry

---

### Post by FCnix on 2005-08-16
thanks, that helped :)

but i can't ping anything... so my network settings seem to be still wrong and i have no clue where to begin - those 4 numbers i posted will get me to internet under Windows XP - well XP can connect to internet even with "auto detect" settings :|

stupid XP ](*,)

---

### Post by cwaldbieser on 2005-08-17
[QUOTE=FCnix]thanks, that helped :)

but i can't ping anything... so my network settings seem to be still wrong and i have no clue where to begin - those 4 numbers i posted will get me to internet under Windows XP - well XP can connect to internet even with "auto detect" settings :|

stupid XP ](*,)[/QUOTE]
From the Kubuntu konsole, post the output of the following commands:
```
$ ifconfig -a
$ route
```
That will give us a good idea of your network situation on Kubuntu.

Also, if you would briefly describe the physical connections (what connects to what, and if it is via ethernet cable, wireless, etc.), this can sometimes be very useful information.

---

### Post by FCnix on 2005-08-17
i messed around with my nw settings some more: changed the broadcast ip and DNS settings and now it works :-P 


ipconfig -a doesn't work but the route function does and displays my ISP name under the Gateway:[list]gw.my_ISP_name.lan[/list]thanks :)

---

### Post by cwaldbieser on 2005-08-17
[QUOTE=FCnix]i messed around with my nw settings some more: changed the broadcast ip and DNS settings and now it works :-P 


ipconfig -a doesn't work but the route function does and displays my ISP name under the Gateway:[list]gw.my_ISP_name.lan[/list]thanks :)[/QUOTE]

That's because the command is "ifconfig" on *NIX and Mac OS X, and "ipconfig" on Windows.  The options probably vary between them all.  Good to see your problem, solved!

---

