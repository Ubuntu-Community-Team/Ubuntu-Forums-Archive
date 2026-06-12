---
title: "Samba problem - keeps cutting off transfers after 1 minute or so"
date: 2009-01-17
forum: General Help
---

### Post by Zarok on 2009-01-17
I don't know if this is the right forum, but I'm not using the server edition either so decided to put this here.

So. Earlier today I got the brilliant idea of setting up my new laptop as a file server to stream videos and mp3 files across my network, rather than storing them on all my pcs. I chose my old Eee PC 701 on it, installed ubuntu on it and stuck on a 500GB LaCie USB drive and got to work. 

I installed Samba, got it working, as in I manage to log in to the share. I setup fstab to automount the sharing with the command(removed the username/pw I use):
```

//192.168.11.7/lacie /media/samba cifs rw,user=username,password=password  0 0

```
Everything was fine and dandy in the world, except when I tried to actually use the share for streaming a file like I wanted to/browse the share. It constantly freezes for like 5 seconds. If I try to transfer a file, it transfers like 100megabytes, freezes for 30 seconds, transfer another 50 megabytes, freezes, etc. You get the picture.

Samba's log file has the following all over it:

```

[2009/01/18 03:40:32,  1] smbd/service.c:close_cnum(1405)
  192.168.11.9 (192.168.11.9) closed connection to service lacie
[2009/01/18 03:40:41,  1] smbd/service.c:make_connection_snum(1194)
  192.168.11.9 (192.168.11.9) connect to service lacie initially as user mie (uid=1000, gid=1000) (pid 21432)
[2009/01/18 03:42:01,  1] smbd/service.c:close_cnum(1405)
  192.168.11.9 (192.168.11.9) closed connection to service lacie
[2009/01/18 03:42:46,  1] smbd/service.c:make_connection_snum(1194)
  192.168.11.9 (192.168.11.9) connect to service lacie initially as user mie (uid=1000, gid=1000) (pid 21700)
[2009/01/18 03:43:15,  1] smbd/service.c:close_cnum(1405)
  192.168.11.9 (192.168.11.9) closed connection to service lacie
[2009/01/18 03:44:00,  1] smbd/service.c:make_connection_snum(1194)
  192.168.11.9 (192.168.11.9) connect to service lacie initially as user mie (uid=1000, gid=1000) (pid 21797)
[2009/01/18 03:44:30,  1] smbd/service.c:close_cnum(1405)
  192.168.11.9 (192.168.11.9) closed connection to service lacie
[2009/01/18 03:45:16,  1] smbd/service.c:make_connection_snum(1194)
  192.168.11.9 (192.168.11.9) connect to service lacie initially as user mie (uid=1000, gid=1000) (pid 21894)

```
From what I can understand from that, as I've never used Samba before, is that its constantly logging me out and logging me in to the share, causing the delays. FTP transfers from the file server to my desktop are fine, they were moving at a good 11mb/s, pretty much what I'd expect from a 100mb internal network. 

I'd just really love to get samba shares to work, so I could stream the files, rather than constantly download them to various machines, and 30 second freezes every few minutes when listening to / watching something just isn't acceptable. Any ideas on how to fix it? My smb.conf at the moment is the default one that came when I apt-get samba, only changes I did to anything is create the user and password I use.

Edit: When I looked at /var/log/messages, I found loads of an error that looks something like this around the time when I was transfering:
```

Jan 18 03:43:21 EeePc701 kernel: [112892.904251] txd read ptr: 0xc28
Jan 18 03:43:21 EeePc701 kernel: [112892.904256] txs-behind:0x000105ea
Jan 18 03:43:21 EeePc701 kernel: [112892.904261] txs-before:0x00010285
Jan 18 03:43:32 EeePc701 kernel: [112903.560113] eth0: txs packet size do not coinsist with txd txd_:0x00000036, txs_:0x0001030c!

```

This issue might be related to [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/147639](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/147639) and the NIC card in question in that, but all other network usage from said computer, other than samba, works perfect.

---

