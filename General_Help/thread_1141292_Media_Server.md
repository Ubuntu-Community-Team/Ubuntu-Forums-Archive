---
title: "Media Server"
date: 2009-04-28
forum: General Help
---

### Post by goldleader on 2009-04-28
Im setting up a media server using ubuntu 8.10 and have a few setup issues i will explain what im tring to achive and hopeful someone will be able to help.

Im installing ubuntu 8.10 with mediatomb to stream media to my PS3 and Transmission to download torrents. I want a headless server running at runlevel 3 so i can then RDP onto the server from another PC on the network to control it.

The problems im facing are as follows:

First off im tring to get everything working in runlevel 5 before i move to runlevel 3.

I have mediatomb running fine as the loged in user but can't get it to run as a daemon.

I don't know how to get Transmission to run as a daemon? I know that i have to create a script in /etc/init.d, however i have no idea what to create in this script. An example of what to do would be great or someone who has already done this would be even better. I know there is a Skeleton file but it doesn't really help. Also running Transmission as a daemon will it allow me to login to the server using rdp and add torrents?

Last problem or more a question as i haven't tried it, if the server is running at runlevel 3 can i connect to it from an Ubuntu 8.10 PC using RDP and login and get a gui? Also will i then be able to open Transmission and add torrents or would i only be able to add torrents using the web page as its running as a daemon, and when i logout of the current session the Transmission will close and the Torrents removed? Sorry of that sounds a bit confusing.

If there is any better software or way of doing any of the above im open to any suggestions.

Thanks.

---

### Post by wesg on 2009-04-28
How did you install Mediatomb? the mediatomb-daemon package from the repositories should work. Are you using a GUI on the server? If you want to control it that way, install a VNC daemon and you can connect to it from another computer on the network. If you have just the command line, use SSH and you can connect to the computer directly. 

Does Transmission work as a daemon? A lot of people - and I'm planning on using this setup too - use Screen with a torrent client to work on the command line in the background. THat would work.

---

### Post by mb_webguy on 2009-04-28
If you're using a headless server, I'd suggest using Deluge as your torrent client.  It has a much better CLI interface than Transmission.  It also has a good web interface, and is more configurable than Transmission.

You might want to consider upgrading to Jaunty.  The version of Mediatomb in Jaunty sets itself as a demon by default.  (Which in my case I *didn't* want, and had to use sysvconfig to disable it.)

Speaking of sysvconfig, how are you editing the runlevels?  If you're trying to do it by hand, I highly suggest trying sysvconfig.  I don't think it's installed by default, but it's in the repos.  It's a menu-driven CLI utility for configuring run levels and services, and quite handy.

---

