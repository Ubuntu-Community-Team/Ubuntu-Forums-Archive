---
title: "rtorrent connection"
date: 2006-10-03
forum: Desktop Environments
---

### Post by neumeka on 2006-10-03
I am having problems dowloading torrents with rtorrent.  I can't seem to ever get a connection.  I am behind a DHCP router, but I have forwarded my ports correctly, so I don't think that the router is causing the probmlem.  What do the two IP addresses ("bind listening sockets to this IP" and "change IP that is sent to the tracker") mean?  What values should I use for them?

Thanks in advance,
Kyle

---

### Post by neumeka on 2006-10-03
More information on my problem: I have now tried to use btdownloadcurses, but I keep getting a "connection refused" error.  Any suggestions?

---

### Post by konsole on 2006-10-04
> **neumeka said:**
> I am having problems dowloading torrents with rtorrent.  I can't seem to ever get a connection.  I am behind a DHCP router, but I have forwarded my ports correctly, so I don't think that the router is causing the probmlem.  What do the two IP addresses ("bind listening sockets to this IP" and "change IP that is sent to the tracker") mean?  What values should I use for them?

Thanks in advance,
Kyle

If you've never seen a connection then is rtorrent listening on your forwarded port? (netstat -a to check) 

Does the log view in rtorrent show any errors?

If this is all good go check your port forwarding as this is likely not working. Try not to use DHCP while testing if possible.

If your router is handling your NAT correctly you shouldn't need to uncomment the IP stuff in .rtorrent.rc

This link provides some good reading: [http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

Good luck and remember to seed seed seed when u get it working.

---

### Post by legan on 2006-12-22
I'm experiencing the same problem.
I opened port 10250 on my router and mapped it to the ip address of my client.
I can see chunks and other peers, but no downloads...
What can be wrong?

---

