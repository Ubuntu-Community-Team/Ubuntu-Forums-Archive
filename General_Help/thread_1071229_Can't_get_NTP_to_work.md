---
title: "Can't get NTP to work"
date: 2009-02-15
forum: General Help
---

### Post by Cyclone42 on 2009-02-15
I am running a Ubuntu 8.10 installation.  I recently had a feeling that my system clock was off, because TV programs (recorded with MythTV) were not being recorded right.  So I check it by calling
the NIST telephone number at 303-499-7111.  Sure enough, the clock is off by a good 20 seconds or so.  

I set up NTP in a pretty straightforward manner.  I just selected "Time and Date" from the Administration menu, made sure my
time zone was selected right, selected a bunch of nearby time servers, and selected "keep synchronized with internet servers". 
I don't know what else to do.

I don't know if this may be indicative of a problem or not, but I killed the ntp service, then ran:

 ntpdate -o 4 pool.ntp.org
 ntpdate -o 4 us.pool.ntp.org

Each time, I got the same error: "no server suitable for synchronization found"

Any suggestions?

---

### Post by andrewc6l on 2009-02-15
It could be you have some sort of DNS problem. I can connect to the  severs and see them set the time fine (on 8.04):

sudo /etc/init.d/ntp stop
sudo ntpdate -o4 pool.ntp.org

15 Feb 21:49:02 ntpdate[16570]: adjust time server 216.45.57.38 offset -0.061577 sec

What happens if you traceroute pool.ntp.org (or try something else like ntp.ubuntu.com or time-b.timefreq.bldrdoc.gov?)

I was able to set times using a daily job (which also grabbed my listings for MythTV) and ntpdate over dialup... so it's certainly possible, but ntpd should do a better job of keeping the time right once it's talking to good servers.

[Edit] I just did a traceroute, and its >30 hops from me to pool.ntp.org - but only 9 to time-b.timefreq.bldrdoc.gov. You might want to investigate a server closer to you (fewer hops).

---

