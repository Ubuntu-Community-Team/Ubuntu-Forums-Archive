---
title: "ntpdate failure during boot - possible solution?"
date: 2006-01-16
forum: General Help
---

### Post by ``bobby`` on 2006-01-16
Not sure if this is the "best" place for this post but I will go ahead and post anyway :) 

First, I noticed during boot-up that ntpdate was failing.  Now, after some searching through the forums I was unable to find a solution to my problem (most people seemed to recommend ignoring the problem or removing ntpdate from the boot-up sequence).

So, I went poking around and happened to peak at my /etc/networks/interfaces file and found the following:

iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid ESSID
        wireless-key1 KEY

I recalled that this file looked a bit different during one of my previous installations.  Please note that my wireless connection was configured during the install process this time around (and works fine) and I configured it manually last time.

So, I changed my interfaces file to look like this (notice additional line at end):
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid ESSID
        wireless-key1 KEY
        auto eth1

Now, ntpdate no longer fails :)  I am not really sure why this worked but it did.  Any thoughts?

---

### Post by Lambert on 2006-01-16
Lines  beginning with the word "auto" are used to identify the physical
       interfaces to be brought up when ifup is run with the -a option.  (This
       option  is  used by the system boot scripts.)  

So basically when the networking init script runs during boot, it runs the ifup -a command. So your interface is configured and connected during boot. Later in the boot sequence ntpdate runs which it now can connect to the ntp server.

---

