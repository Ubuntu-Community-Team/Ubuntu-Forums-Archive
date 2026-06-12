---
title: "How would you trouble-shoot this no Web?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by dgermann on 2006-07-17
Hi--

Without my server up and running, I cannot connect to the Web with a Web browser. Once the Web connection is made, as long as I keep that computer up, I can shut off the browser, turn it back on, and surf as I want. When I shut off or reboot this computer, if the server is not up, I cannot again access the Web--until I reboot the server, then reboot the client machine, in that order.

Trouble is, my server crashed yesterday.

My server was a Red Hat 9.0 box at 192.168.0.200. My client is an Ubuntu 6.06 at 192.168.0.107. My router (Lynksys WRT54G) is at 192.168.0.1. My other two linux boxes (also Ubuntu 6.06) can get to the Web fine. So can at least one Windows box.

The server is mainly to serve up smb/cifs shares in a production environment. It did not even have X installed.

I have checked network settings and networking from the gnome System > Administration menu on this client box and have found no references to 192.168.0.200--I had thought that perhaps that was set up as my default gateway, but that does not seem to be the case.

How else would you trouble shoot this?

Thanks!

---

### Post by Gordon Farmer on 2006-07-17
When your client 192.168.0.107 can't get out to the web again, try pinging your gateway 192.168.0.1 from the command line...

```
ping 192.168.0.1
```

If you can't connect via 'ping' to your gateway, try resetting it (power off/power on).  Each client box should be able to talk to the other client boxes, and the server too.  I'm talking about pinging each box's IP address from the server and/or other client boxes.

Also check to see that the interface 'eth0' is 'active'.  Look at System > Administration > Networking

Just some ideas... hope you get it figured out.

---

### Post by dgermann on 2006-07-17
Gordon--

Thanks for your quick reply!

Just checked--eth0 is active.

As of now, with the connection to .107 still up, everybody can ping everybody else, at least on a spot check basis. I will follow your advice and do some pinging the next time I have to reboot this machine.

Thanks, Gordon!

---

### Post by dgermann on 2006-07-30
Gordon--

After a reboot can still ping all around.

I am wondering if the problem lies in my router. Is there a way to test the router? (I cannot get any Web nor even ping if I try to bypass the router with the cables.) Is there something I should check for settings on the router? It it a Linksys WRT45G.

I am also wondering if the fact that the router is not at the default address but at 192.168.0.1 could be a culprit?

Anybody any ideas?

---

