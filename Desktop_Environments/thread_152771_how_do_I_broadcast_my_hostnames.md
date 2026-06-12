---
title: "how do I broadcast my hostnames?"
date: 2006-03-30
forum: Desktop Environments
---

### Post by jimbren on 2006-03-30
This is a silly question, but it has been bugging me and I thought I'd throw it out and see if anyone bites. 

I've got a simple wireless network at home with 4 computers: 2 Kubuntu, 1 win2k, and 1 winxp.  I've got a netgear wireless B router that handles DHCP, all works fine.

My 2 Kubuntu boxes don't seem to broadcast their hostnames.  Here's what I mean:
I've got the following machines on the network
smith-->my laptop
trinity-->my wife's win2k desktop
mouse-->my son's kubuntu desktop
jukebox--shared\spare winxp laptop

When I log onto my router and look at the connected devices, I see something like
192.168.0.x  trinity     mac address
192.168.0.x jukebox    mac address
192.168.0.x <blank>   mac address
192.168.0.x <blank>   mac address

When I want to browse for files on another machine, I can browse to trinity and jukebox without an issue just by name, but of course I have to know the IP address for the un-named machines.

I know I could get around these easily enough by just making host file entries on all four machines, and it wouldn't be a big deal.  But it irritates me that I don't know how to fix it.

kisses,

jimbo

---

### Post by ispmarin on 2006-03-30
To browse your files, are you using samba?

---

### Post by jimbren on 2006-03-30
Yes I am.

---

### Post by jimbren on 2006-04-03
I do use Samba to connect to and from my Windoze boxes, but that's not really an issue as far as I can tell.  What I'm really looking for is having my two linux machines broadcast their host name.

Am I going about this the wrong way?

Do I need to have one of my linux machines act as a DNS server on the local network?

---

### Post by Mau on 2006-04-04
I had the same problem.  My solution (I have a 2Wire btw) was to simply tell the router that this IP is this hostname.  It works and I sometimes have to reset it (haven't figured out the pattern).

---

### Post by mooseman089 on 2006-04-04
I follwed these steps and it worked [http://ubuntu.wordpress.com/2006/02/06/fix-hostname-unknown-in-router/]("http://ubuntu.wordpress.com/2006/02/06/fix-hostname-unknown-in-router/")

---

### Post by jimbren on 2006-04-05
Sweet!  Thanks.

---

