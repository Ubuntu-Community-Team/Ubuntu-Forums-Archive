---
title: "Inspiron 1420 wireless"
date: 2007-09-24
forum: Dell  Ubuntu Support
---

### Post by lewindha on 2007-09-24
Hello all

I bought the 1420 with Ubuntu pre-installed about a month ago.  It's been great, but I've begun to have wireless problems.  When I first got it, the network manager would start up and detect the wireless networks available.

But lately, the network manager isn't starting on login.  I have to go to Sysem>Administration>Network and then manually enter my wireless info and then enable it and then I have to reboot.  After rebooting the network manager starts up, but it won't connect.  I have to open the manager and enable roaming on my wireless connection and then it finally works.  

Is anyone else having this problem???

---

### Post by darth_indy on 2007-09-25
I'm having a worse problem. I recently updated the kernel, and on restart the network manager wasn't even showing my wi-fi card! If I use GRUB at startup, to revert back to the original, it works fine, but I don't want to stick around while my computer's booting up sometimes.

My computer is the Dell 1420n with the Ubuntu preinstalled.

Please help!

---

### Post by bindatype on 2007-10-31
This is a reply to the second guy who posted that ubuntu didn't see his card after upgrading the kernal. This happened to my wife's mac when I upgraded to gutsy from feisty. What I did to correct it was open the /etc/network/interfaces file and manually add an entry for eth0. There should be an entry for lo (loop back) which you can imitate...or you could open the file on a properly configured machine and copy and paste. 

And yes, gutsy gibbon does run on PPC but the damn airport card (eth1) still doesn't work...but that is for a different thread.

---

### Post by deserthowler on 2007-11-02
I immediately installed WICD because Ubuntu always opened on the neighbor's unsecured WiFi.  Now I start manually but no reboots or problems.

This is the original /etc/network/interfaces file which works fine:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp
address 192.168.0.201
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0
```

I guess I should add something for the ethernet connection.

Earl

---

