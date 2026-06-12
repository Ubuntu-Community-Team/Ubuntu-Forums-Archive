---
title: "Interface eth0 auto down"
date: 2012-02-01
forum: Desktop Environments
---

### Post by Jay89 on 2012-02-01
Hello,
   I have a ubuntu 10.10 (Maverick Meerkat) box and I noticed that every time the computer boots the interface eth0 is automatically down. I have to manually do an ifconfig eth0 up command every time and that can get very annoying. 

   I checked in the interfaces file and this is what it says.. Am I missing anything?


auto lo
iface lo inet loopback

iface eth0 inet static
address 10.1.0.41
netmask 255.255.0.0
broadcast 10.1.255.255
#network 10.1.0.0
gateway 10.1.0.6

Also, I checked the gui interface and the network information there is correct. Then I double checked the status of the interface after I brought it back up and the BCast address is always 0.0.0.0 for some reason.

Thanks

---

### Post by varunendra on 2012-02-01
Why did you have to put that info in the 'interfaces' file. Usually, it only contains the two lines of loopback interface and nothing else. While the other interfaces are managed by Network Manager. Also, the configuration in the file seems to be of an 'ad-hoc' network. Is that intentional? It seems to have been done manually, because Network Manager never writes to that file.

By 'GUI', I assume you mean the nm-applet (Network-Manager's applet in upper-right corner). If it also contains the same IP configuration, then I doubt you have either some unusual type of network, or some misconfiguration issues, or both.

As for the eth down issue, make sure "Enable Networking" has a tick mark in the right-click drop-down menu of nm-applet, and in the "Edit connection" dialogue-box, "Connect automatically" is enabled for the listed connection(s).

If you are sure the IP configuration is correct and according to your need, then there should be nothing else to change/check.

Else I'd like to know more about what kind of network you have and how have you configured it.

---

### Post by airdelroy on 2012-02-01
I think you can add the following line to make it work.

auto eth0

Aaron

---

