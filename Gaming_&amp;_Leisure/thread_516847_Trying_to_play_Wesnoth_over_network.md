---
title: "Trying to play Wesnoth over network"
date: 2007-08-03
forum: Gaming &amp; Leisure
---

### Post by geek_Man on 2007-08-03
Hi all, I've been trying to play Battle for Wesnoth over my local network, only I don't know how to set it up. Obviously I have two computers, one that's hosting and one that 's joining, but I can't seem to connect to the hosting computer. Can anyone give me any insight on how to do this? I know that this probably isn't the best place to find this out, but I think Ubuntu Forums is the best. Thanks in advance!

---

### Post by geek_Man on 2007-08-08
Anybody...?

---

### Post by Ozor Mox on 2007-08-08
There are two ways. The easiest way is to click Multiplayer > Host Networked Game on one computer. Once you have set up the game and you are on the screen where you can see the list of players, on the other computer click Multiplayer > Join Game. On the hosting computer, type ifconfig into a terminal to find out the local IP address for that machine (for example 192.168.0.10). Type that in to the box on the joining computer.

The other way is to run wesnothd from a terminal to start a Wesnoth server on port 15000. Then on each computer on the network, click Multiplayer > Join Game and type in the server's IP address (find that out using ifconfig on the server machine as above). If one of the computers you are playing on is also running the server, on that one you can type in localhost instead of the IP address.

Wesnoth doesn't yet have automatic detection for LAN games, so you have to put in local IP addresses, though I think the feature has been proposed. Still, both Linux and Windows make it easy to find your IP address :)

---

### Post by geek_Man on 2007-08-09
Thanks, Ozor, I'll try that out! When typing in the IP address of the host machine do I have to add the port number? Like 192.168.1.100:15000?

---

### Post by geek_Man on 2007-08-09
Youdaman, Ozor. I got it to work. Thanks!

---

### Post by Ozor Mox on 2007-08-10
> **geek_Man said:**
> Thanks, Ozor, I'll try that out! When typing in the IP address of the host machine do I have to add the port number? Like 192.168.1.100:15000?

I know you have it working now, but I just thought I'd say that you only need to add the port number if it is not running on the default port, which is 15000.

Glad I could help :)

---

