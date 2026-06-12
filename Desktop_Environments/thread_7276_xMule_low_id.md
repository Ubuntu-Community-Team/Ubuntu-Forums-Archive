---
title: "xMule low id"
date: 2004-12-05
forum: Desktop Environments
---

### Post by Pulka on 2004-12-05
Hi there!

Lately i'm having problems connecting to servers in xMule. In the log, it says i have a lowid, but i didn't change anything.
For what i know, that lowid is caused by a firewall or the safe connect in xMule. I have safe connect turned off, so it has to be from the firewall.
How can i know if i have a firewall installed?
If it isn't from the firewall, does anyone have a clue of what's the problem?

---

### Post by KrIaXPaTaLa on 2005-02-15
I have the same problem connecting to some servers. I've forward the udp/tcp ports in my router, but that didn't seemed to work. Ubuntu aparently doesn't come with any firewall, so in my case, I dont have a clue to what might be wrong. U should check your router ports, though. Might work in your case. Normally U need port 4662 TCP and 4672 UDP opened for emule clients to work. Good luck.

---

### Post by piedamaro on 2005-02-15
To see if you have a FW running do:
sudo iptables --list

if it yelds:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

you have NO firewall.

...and use aMule!

---

### Post by theh0g on 2005-02-15
I've just solved the same problem: some ISPs block certain ports, but I've found some page where it said port 25600 usualy works on ISPs, that block osme p2p programs. It sounds weird, but it worked! Try it, it can't hurt :)

edit: yeah, use aMule and install wxGTK2 v2.5.3 before compiling it, so you can get a nice GTK2 look :)

---

### Post by lothar_m on 2005-05-09
hello

i'm having the same problem here.

i'm running hoary with amule 2.0.0 and it always gives me low id when connecting to a server. My router has port forwarding correctly configured but the emule server can't reach 4662 tcp port. i've tried changing ports but without luck.

a couple of weeks ago i was running warthy with xmule and everything seemed ok. since the upgrade to hoary and amule it doens't connect.

I suspect that somehow hoary is blocking the acess but i can't figure it out. As far as i can tell iptables is not active.


help appreciated!
thanks.

---

### Post by zeroverse on 2005-10-08
I use amule and I was having a mysterious lowid problem.  I also had "firestarter" installed, so I got rid of it since I didn't really need/use it...and my high id is back.  Check to see if you have a firewall program installed and configure it correctly (or remove it).

---

### Post by autonomy on 2005-10-28
I've stopped my Firestarter, and my aMule still didn't get green arrows. I've allowed 4662, 4672, and 4665 and even allowed the particular IP that I'm using, but my arrows are still yellow. I also clicked on "Apply Policy" and restarted my GNOME.

---

### Post by JurB on 2005-11-10
Do you have a direct connection to the internet or are you using a shared connection in a LAN?

---

### Post by autonomy on 2005-11-10
I have DSL, so I guess that's a direct connection; but when I had cable, he said, call it a LAN when prompted. Limewire works pretty good for me, so I think it just has something to do with Mule and my firewall.

---

### Post by JurB on 2005-11-10
mmm ok, i had problems whith low-id on my pc cause i was in a lan because i didn't have a direct connection to the internet. When i run it on the pc with the modem attached to it it's no problem.

---

### Post by Avatar on 2005-11-21
Well, I'm using a shared connection in a lan and I can't obtain an high ID.. 
I've stopped firestarter on the server but that doesn't seem to have any benefict :\

any suggestion?

---

### Post by lothar_m on 2006-11-26
> **JurB said:**
> mmm ok, i had problems whith low-id on my pc cause i was in a lan because i didn't have a direct connection to the internet. When i run it on the pc with the modem attached to it it's no problem.

my situations is the same. 

when i connect my modem directly to my pc everything runs smoothly (high id and high transfer speeds). However when connected through my router (dlink 624+) i always get low id and low speeds. 
after a lot of research i believe that somehow my router isn't able to deal with a high number os connections at the same time. there for is not suited for p2p traffic.

---

