---
title: "remotely login to a Ubuntu 16.04 desktop with new session"
date: 2016-06-16
forum: Desktop Environments
---

### Post by victor.cighir on 2016-06-16
Hello ubuntu friends!

I've been a long time Ubuntu user, almost 9-10 years now. Anyway my 5 year old laptop isn't doing such a good job at anything but surfing with 1-2 tabs lately, so I decided to buy a PC. The configuration is an Intel Core i7 6700 with 8 gigs of Ram and intel HD530, 250 Gb SSD, connected to a UHD 4k TV by HDMI cable. Everything nice so far, working as a charm. 

It turns out, that my wife doesn't like sitting in front of the TV so she wants to buy a Monitor. 
I've got a better idea > use the old laptop to remotely connect to a new session on the PC, with another user as the one currently logged in and of course full-screen. The resolution has to be of course adapted to the smaller display of my laptop. 

As always searching the Internet hasn't got me too far.... I couldn't get VNC (vnc4server) to work properly (unity does not start, although I uncommented the 2 lines in the vnc config file), Thin client is too much overhead, default Desktop-Sharing from Ubuntu gives me an error "Server did not offer supported security type".

Does teamviewer enables me to connect and log in to a user, or only to the current desktop?

Please help me guys!! 
Thank you so much!

---

### Post by TheFu on 2016-06-16
Don´t use unity on any remote desktops, period.  
VNC is kinda slow.
The easiest, fastest, most secure, answer I know is to use x2go. There is a server for the remote box and a client for the laptop.  I use this daily for many hours, from between 2 ft away and 14K miles away.
[https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/](https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/)

Keys to this are:
* use a lite desktop - LXDE or XFCE are best supported.
* setup ssh with key-based authentication first.  x2go will use those same keys on Unix client systems.
* On Windows clients, install the special font packages.
* After things are working, tune the connection speed for the true connection speeds available.  I have different connections for LAN vs WAN. On WAN connections, I use ISDN as the available bandwidth just to ensure the compression expects a limited network. Watching video doesn´t work over the WAN, but does work poorly over a GigE LAN. 

No need to trust someone like teamviewer for this on Linux.  Think of all the things you are trusting when allowing a foreign entity this sort of access.

---

