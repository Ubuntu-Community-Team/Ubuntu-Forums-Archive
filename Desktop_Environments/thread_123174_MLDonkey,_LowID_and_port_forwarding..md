---
title: "MLDonkey, LowID and port forwarding."
date: 2006-01-29
forum: Desktop Environments
---

### Post by z-vet on 2006-01-29
Here's a (wired) LAN my ISP installed for me to allow two computers (both running Kubuntu Breezy) in my house to share the same connection. I wanted my mother, which uses a second machine, to have an MLDonkey, so i installed it for her, completely forgot about a multi-user functionality (stupid me, just needed to add her as user to my existing client). I think here's something went wrong, because now both clients have LowID from all servers. I completely sure that the problem appeared after i started a second MLDonkey: i just installed and started it, restarted one running on my machine and found that everything is screwed up. I can't find what is wrong and need help. I asked on MLDonkey forums and an answer was to check my firewall, but i don't have firewall at all (well, maybe a router's built-in, but why it did not blocked ports before?). Later today some friend of mine told me that i need to configure port forwarding, but i really have no clue how to do it... :cry: 
Please, point me to some "idiot's guide to port forwarding" or something...

---

### Post by obibok on 2006-01-29
This is not the best place to ask for help with your problem as it's not really Ubuntu related.

Anyway, just to shed some light... you can only have one client use a specific port, which in case of the eDonkey2000 network is 4662. If two or more clients try to use the same port, you'll have a problem.

One possible solution would be changing the default port for the network you connect to in MLDonkey on one of your systems. You may also need to find out how your ISP set up your LAN and change the "public" port there.

---

### Post by z-vet on 2006-01-29
Trying to fix it... Thanks for reply.

---

### Post by nalmeth on 2006-02-09
I see nothing wrong posting this question here. Maybe the networking forum, but if the guy's using ubuntu, its ubuntu related. 
I can't help you much, though. Have you figured it out? I know you can log in to your router through a browser like firefox, but I think most routers are set to allow typical p2p connections.

---

### Post by z-vet on 2006-02-09
Ok, it looks like my router was confused by two clients running side-by-side and locked ports automatically. Reset and RTFM were my friends, i forwarded appropriate ports, uninstalled client from second computer and configured one running on my machine to allow connections from local network. Everything works fine now. :)

---

