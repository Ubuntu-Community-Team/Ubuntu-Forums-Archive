---
title: "Is there an update in 8.10 that disables your network connection?"
date: 2009-02-12
forum: General Help
---

### Post by Roasted on 2009-02-12
There's a couple of network based applications we'd like to try out at work here but they require an Ubuntu server. The network admin is working with Ubuntu in a virtual machine to do some testing and get to know the OS better. He just emailed me and can't figure out why his network connection dropped. The only thing he can think of that he did was scanned for updates. 

I do not believe he is using network manager. I believe he edited the network file manually, which I even reviewed it, and it does look perfectly fine and was functional for quite some time.

Any ideas?

EDIT - We disabled network manager upon startup. Didn't make any changes. Under ifconfig, eth0 doesn't appear. We ran the command etho0up or whatever it is. Even after a reboot, nothing changed. It's as if the card simply isn't turning on now. When we put the LiveCD into the computer, the internet connection works fine. However, when we boot Ubuntu 8.10 32 bit up through VMWare Server 2, the network icon is just completely grayed out in the VMWare toolbar, and within Ubuntu, like I said, eth0 is completely... not there. 

This was a fresh install of Ubuntu 8.10 32 bit on an Optiplex 755. Over 100 updates were downloaded on Tuesday, February 10th. That's when the problem started happening. The Optiplex 755 has a Broadcom network card.

---

