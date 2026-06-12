---
title: "Speed up Samba and file sharing processes"
date: 2006-09-18
forum: Desktop Environments
---

### Post by benjaminwr on 2006-09-18
Hi, I have a problem at work. I have been trying to set up a samba file server to centralize all files in our office, but I constantly get the problem of the server locking up when I get 2 or 3 simultaneous connections. The Server has a normal desktop ubuntu installed since it is also used from time to time as a workstation. So i don't want to install the ubuntu server version.

Is there any way I could prioritize samba file sharing over anything else on that system.

Cheers

---

### Post by kidders on 2006-09-18
Installing Ubuntu's server version won't impact your ability to use it as a workstation.

To reprioritise processes, use the "renice" command, although I doubt doing that will help you :-( What do you mean by "locks up" exactly?

---

### Post by benjaminwr on 2006-09-18
the server itself doesn't lock up, but the clients do. The window that is trying to show the files on the server just locks up. I suppose because samba is trying to serve something that it can't cope with so clients just keep waiting but never receives what it asked for.

But isn't the server version only command line?

cheers

---

### Post by jethro10 on 2006-09-18
I also got this on a SAMBA based NAS device at home.

For me, it was Gnome/Nautilus.
I installed KDE and it worked like a charm and much faster.

You could try it to prove a point. It may get you a step closer.

J

---

### Post by kidders on 2006-09-18
Yep, afaik the server edition is pretty lightweight, but installing a pretty graphical environment on one shouldn't be rocket science, I'd say. In that respect, there's not much difference between Ubuntu variations.

In any case, it probably wouldn't solve this samba issue. The thing to do is to try to find out exactly where the bottleneck is. Here are some possibilities:

[LIST=1]
[*]Samba is configured to accept a stupidly low maximum number of connections.
[*]Samba needs your entire CPU to handle 3 connections, so 4 is just out of the question.
[*]Your disks are slow, very badly fragmented or too busy to manage lots of clients.
[*]Your network infrastructure is faulty or badly designed, and drowning in TCP retransmissions of garbaged data.
[*]Your network is just too slow.
[/LIST]

Jethro10 makes a good point, in that some filesharing clients are more efficient than others. If your clients are Windoze boxes, you don't have much choice though :-(

Here are some basic things you can do to help diagnose your problem:

[LIST=1]
[*]Monitor your CPU usage on the file server, especially the CPU waiting time (ie %age cycles wasted waiting for I/O operations).
[*]Install ethereal and take a look at what's *really* going on on your LAN.
[*]Replace badly positioned hubs with switches.
[/LIST]

Based on what you find, it may be worth experimenting with mirroring, for example ... perhaps with RAID.

**Edit:** In addition, samba has a range of options you can set to try to optimise how it manages I/O. These include changing the I/O buffer size, using asynchronous I/O, keepalive and socket-related settings. Tinkering with them can make a *big* difference to performance.

---

