---
title: "Internet Connection Sharing - NEED HELP!"
date: 2009-06-04
forum: General Help
---

### Post by pro003 on 2009-06-04
Internet Connection Sharing - NEED HELP!
Ok. Here's the trick. I have a wire from an ISP through which I connect to internet using PPPoE protocol and this should be adjusted on Linux (Ubuntu) box. While from this box the ethernet cable goes to switch and from switch the other machine needs to have access to internet. Also the Linux box should play a role of file server and as said an internet gateway.

If you are not sure what I want to achieve, look at the picture:


[[IMG]http://img294.imageshack.us/img294/5134/snapshotw.png[/IMG]](http://img294.imageshack.us/i/snapshotw.png/) [[IMG]http://img294.imageshack.us/img294/snapshotw.png/1/w649.png[/IMG]](http://g.imageshack.us/img294/snapshotw.png/1/)


Basically, I want the first box to be under Ubuntu (Jaunty Jackalope -with Gnome), then I want to establish PPPoE connection to Internet using integrated NIC, and then I want to share (masquerade) internet from this box with other machines on network through / via PCI NIC > SWITCH.

English is not my native language, so sorry if I was maybe less clear.

Waiting for your help.

Thanks!

---

### Post by blueridgedog on 2009-06-04
I assume that the ISP connection is up and working and that you have a fixed ip on the PCI nic using private address space (192.168.1.1 for example). 

To get the Linux system to serve as a router, you need to setup NAT using iptables.

The first step would be some of the good howto's on the net:

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

and

[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

and 

[http://www.howtoforge.com/nat_iptables](http://www.howtoforge.com/nat_iptables)

There are many more you can get from google with a search on "Linux iptables nat".

The systems downstream of the Ubuntu box will use the fixed ip of the server as the gateway.  They will all need to share the same addressing scheme.

Prior to trying to make routing work, you should get the basics of the network setup and working so that all systems can ping each other and generally work without the NAT.

Once you have your NAT commands down, you can put them in a configuration file so that it is easy to launch it each time you restart the system.

---

### Post by Boondoklife on 2009-06-04
Check out Firestarter, It allows you to manage iptables easily. I have not used the NAT option but there is one in there.

---

### Post by pro003 on 2009-06-05
thnx blueridgedog, I'll take a look at these links and post results later today or during the next few days when I finish the work. I didn't even started yet, so I know all about iptables and yes I know about its frontend firestarter which I use regularly, but this is a precaution measure, I always do the google but sometimes I just like a nice piece of advise right from here, the ubuntu forums!

thnx!

---

