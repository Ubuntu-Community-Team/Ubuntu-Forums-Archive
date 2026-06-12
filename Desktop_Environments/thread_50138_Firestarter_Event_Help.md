---
title: "Firestarter Event Help"
date: 2005-07-19
forum: Desktop Environments
---

### Post by YaAqoB on 2005-07-19
Hello all. I'm wondering if anyone can explain the events getting blocked by Firestarter in the screenshot below. Its only just started yesterday.

Cheers

[Screenshot](http://www.nabc.org.nz/firestarter_events.png)

---

### Post by bk452 on 2005-07-19
I'm new at this also, but this might help a little bit:

[http://www.ubuntuforums.org/showthread.php?t=49185&highlight=firestarter+block](http://www.ubuntuforums.org/showthread.php?t=49185&highlight=firestarter+block)

---

### Post by mad_scientist03 on 2005-07-19
It looks like your firewall is blocking continued attempts to connect to your Samba server. Do you have a Samba server running? The "Source" of 10.0.0.3 looks like a private source to me, but I'm not sure about that. 

You can always go <a href="http://www.geobytes.com/IpLocator.htm?GetLocation">here</a> to try to locate any of the non-private IP addresses that show up in your firewall logs. Is this computer in an office, or on some sort of private network? Are there Windows machines around? Windows machines can push a lot of noise out to the network, and those Samba connection attempts may be the result of that garbage.

The only legitimate block from your firewall looks to be against the IP 69.196.236.233. Depending on how your firewall is setup, you can look at /var/log/kern.log or /var/log/auth.log for the logged output of what your firewall is blocking. You can get more information from the logs, like what ports were trying to be connected to, etc.

Does FireStarter sit on top of an iptables rule set?

---

### Post by YaAqoB on 2005-07-19
10.0.0.3 is the IP that my router has assigned me.
Thanks for your help. I'll look into how to stop Samba server untill i actually need it.
Cheers again.

---

