---
title: "Portable Ubuntu - Internet Connectivity?"
date: 2009-04-10
forum: General Help
---

### Post by Mehall on 2009-04-10
Right, so I couldn't really tell where to put this, since it's not an official version thingy or anything, but I'm trying to use Portable Ubutnu For Windows (the thing that uses colinux and XMing to run Ubuntu inside Windows, but not as a VM)

I have no Internet connectivity inside the Ubuntu, but it's fine on the "host" machine. Any clues?

And sorry if this is the wrong place, but I didn't have a clue where to put it

---

### Post by Mehall on 2009-04-10
Damn double NAT caught me out.

Discovered I could access inside my network, as that was only one layer of NAT, and then I used an ssh tunnel to the box I use for DNS on my network, and set it as the global proxy (gnome-network-preferences) and put that server's IP into /etc/resolv.conf to make sure it would be used for DNS rquests.

---

### Post by naisanza on 2009-04-29
Hey, I have probably the same problem you initially had with portable ubuntu.
 
 Essentially, I can direct connect to any web sites via their ip address. What can I do to get it to use the proper dns?
 
 I don't exactly know what I'm doing.
 I added nameserver 208.67.220.220 to resolv.conf and it shows the dns under network-admin.
 I'm stumped so I started having fun and added some addresses to the hosts file.
 
 I think you created an ssh tunnel to your dns box (but I don't have one).
 
 Thanks really appreciate any help

---

