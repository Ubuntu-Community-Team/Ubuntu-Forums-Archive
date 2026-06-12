---
title: "Very slow server access after change of router and IP range"
date: 2009-02-02
forum: General Help
---

### Post by dumb on 2009-02-02
Hi,
I have a server running Ubuntu 6.06, which is used for many things fx. fileserver, mailserver, MythTV backend, printserver, webserver. It's been working great, with no problems at all. But one day, I decided to change my router from a SMC 10/100, 54mbit wireless to a D-Link DIR-855 10/100/1000, draft-n wireless and with that, I also changed the IP range from 192.168.1.x to 192.168.0.x, because that was the default of the new router. So all clients, including my server, on the network got new IP adresses.

But after changing router all access to my server has gotten extremly slow. Especially when my clients try to NFS mount to the server, first time it always times out but if I try again, it connects. Also, I'm running a CUPS server on it, for sharing my printer and connecting to the web admin of CUPS, takes like forever, it's running on the default port 631. SSH login to my server has also increased. My server is not connected through wireless and it has only got a 100 mbit ethernet.

When I get connection, transfer speed seems to be normal.

Anyone got any bright ideas as to what is going on?

---

### Post by dumb on 2009-02-05
No one, with any bright ideas?

---

