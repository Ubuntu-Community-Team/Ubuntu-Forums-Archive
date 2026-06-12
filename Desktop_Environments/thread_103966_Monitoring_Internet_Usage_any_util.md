---
title: "Monitoring Internet Usage: any util?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Ananth on 2005-12-15
Hi,

Is there any utility to monitor the internet usage?

We have an ADSL connection, which we have configured using pppoeconf and using pon/poff for connecting to the net. The problem here is, we are not able to check how much data is uploaded/downloaded.

Our ISP (BSNL, India) sets us a limit of 1 GB/month transfers, but there's no limit for usage from 2 AM to 8 AM daily. Unfortunately, our ISP doesn't provide us clear statistics about our late-night free usage.

So, is there any tool available for ubuntu,

    * which shows the total data transfer for the current internet session,
    * and also help us to find out the total usage for the month excluding select hours


Thanks in advance,

Ananth.

---

### Post by gilgongo on 2005-12-15
You could try the webmin-bandwidth module. I've not tried it, but it says in Synaptic:

This module allows webmin (a web-based interface for system administration
for Unix) to report on bandwidth usage by host, port, protocol and time.

---

### Post by sudharshan on 2005-12-15
webmin is a perfomance hog..
try vnstat instead...it operates within the terminal and whats better...?
it doesnt run as a background process since it reads the data from the /proc filesystem...

```
sudharsh@acidlabs:~$ vnstat
Database updated: Thu Dec 15 18:00:13 2005

        ppp0

           received:         310.44 MB (92.8%)
        transmitted:          24.91 MB (7.2%)
              total:         335.35 MB

                        rx     |     tx     |  total
        -----------------------+------------+-----------
           13.12.     13.08 MB |    0.48 MB |   13.57 MB
            today         0 MB |       0 MB |       0 MB
        -----------------------+------------+-----------
        estimated         0 MB |       0 MB |       0 MB

```

i beleive u r looking for a tool like this

---

### Post by jmcelroy on 2005-12-15
'ifconfig <network interface>' will tell you the total number of packets/bytes sent and recieved for a network interface.  If ppoe is creating a new ppp connection (I assume it does), then you could read that.  With a little bit of scripting you could automate the process nicely.

try ifconfig ppp0 for starter and see what you get.

---

### Post by gilgongo on 2005-12-15
The OP wants to know their bandwith use at specific points in time during the day, so what we're saying is there's no easy solution to that unless they use webmin.

How about SNMP?

---

### Post by nix4me on 2005-12-15
I use the KDE system Guard to monitor my network traffic.

It gives nice streaming graphs.

All you have to do is apt-get it and add network device inbound and outbound graphs to the display.

nix4me

---

### Post by Ananth on 2005-12-15
[QUOTE=jmcelroy]'ifconfig <network interface>' will tell you the total number of packets/bytes sent and recieved for a network interface.  If ppoe is creating a new ppp connection (I assume it does), then you could read that.  With a little bit of scripting you could automate the process nicely.

try ifconfig ppp0 for starter and see what you get.[/QUOTE]

thanks jmcelroy, ifconfig is just simple and cute.

Ananth

---

### Post by Ananth on 2005-12-15
[QUOTE=sudharshan]webmin is a perfomance hog..
try vnstat instead...it operates within the terminal and whats better...?
it doesnt run as a background process since it reads the data from the /proc filesystem...

i beleive u r looking for a tool like this[/QUOTE]

exactly! :D 

Any idea about how to use the -q (query) thing? I guess this query or '--dumpdb' will be useful to calculate my night-usage.

Thanks.

Ananth

---

### Post by BatsotO on 2005-12-15
Multi Router Traffic Grapher ?

---

### Post by LanceRushing on 2005-12-16
There is also iptraf.  It's a command line monitor, it can also log for later analysis. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=4563&stc=1&d=1134717518[/IMG]

```
sudo apt-get iptraf
```

---

### Post by SpiritIsReality on 2007-10-11
howdy
when you know how many packets you have received over a length of time, how do you know how many GB you've just added to your monthly total. we're limited to 60 GB/month . I guess look it up on the account at your ISP before and after just like a before ifconfig and after config?
have to look into the ot her options mentioned on thread. thanks for the archive.
trails
buds

---

### Post by Ananth on 2008-04-10
update: (after 2 years!)
The ISP provides free & chargeable usage statistics now. (Buggy, minimal, but usable  info :) Tariff plans and limits have changed.

The topic is still open. A tool for monitoring and managing internet usage will be of great use for millions of people using limited internet connections.
[LIST=1]
[*]Monthly usage allowance (in MB/GBs or Hours)
[*]Free hours
[*]Warning as limit approaches
[*]Ability to restrict and schedule download managers and torrent clients
[*]Ability to connect to/disconnect internet by rule set by the user
[*]Combining statistics from networked machines sharing the same internet connection
[*]Ability to import & combine usage statistics data from other distro/windows in the same machine[/LIST]A tool with features mentioned above will be great for monitoring and controlling internet usage according to the limits imposed by the users tariff plan.

---

### Post by Confuzius on 2008-04-11
It sounds like custom router firmware might suit you better.
[http://www.dd-wrt.com/wiki/index.php/Main_Page](http://www.dd-wrt.com/wiki/index.php/Main_Page)

---

