---
title: "FTP:netout: Connection reset by peer"
date: 2009-01-04
forum: General Help
---

### Post by Eviltechie on 2009-01-04
I wrote a script to first tar /home, then copy it to my nas via ftp. Obviously copying 58gb will take a while, so I left it to run at night. When I came back, the last line said "netout: Connection reset by peer" and my 58gb tar was nowhere to be found. What exactly happened here? And how do I prevent it from happening with my cron job that runs in 40 min.

Update: I asked my dad about this, and he thinks it is a fluke. FYI, the timeout on the ftp server is 10 minutes. Would this be a problem?

---

### Post by sheph on 2009-02-19
I don't think it's a fluke.  It's probably not related to the time out either.  I happen to be getting it in scp to transfer a large number of files (8G) between 2 Ibex servers.  It doesn't matter which side I initiate from, and it doesn't matter if I use the host names or IPs (although with the IP I can transfer more data before it resets).  I started searching in google and found that this is an issue that spans linux distributions, as well as applications.  It seems that TCP/IP under linux in general does not handle large data transfers very well.  There has been some talk that it might be related to the stack itself, but I've yet to find someone that says "this is what you do to fix it."

---

### Post by sheph on 2009-02-19
Ok, I stand corrected.  In my case, it turned out to be a problem with either the NIC or the port in the switch.  It's a multihomed machine.  Using the other interface I can transfer lots of data all day long.

---

