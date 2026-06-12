---
title: "SMB file share suddenly available only by IP"
date: 2008-12-28
forum: General Help
---

### Post by dcmcderm on 2008-12-28
So I logged into my laptop this morning to access the shared folder I have on my ubuntu server and found that my macbook couldn't find the server.  After a bit of fumbling around I discovered that I could connect to it by using the IP address instead of the hostname.

What gives?

I have spent the day reading various other threads on this, and most often it seems to be caused by some sort of update (like an OS upgrade or update to samba).  The thing is for me, I haven't done anything, ie not one single thing, to either my server or laptop since the last time I connected, a week or so ago.  Hence the other suggestions don't seem to help.

I can ping by IP, but not by hostname.  I have a shared printer hooked up to the server and it works fine as well, set up by hostname.

The only odd thing I have noticed, is that way back when I upgraded to 8.10, I tried to set a static IP, which wouldn't work and I discovered it is a known bug.  Rather than muck with the networking config files I just settled for DHCP.  Well today lo and behold the server now has the static IP that I tried to set back in the fall.

Any suggestions?  

PS I have been fumbling my way through linux for 2 years now and this is the first time I've had to resort to asking for help...the forums have always come to the rescue!

---

### Post by pietjanjaap on 2008-12-28
Check your firewalls on both pc/mac, looks like dns(or name resolving) is not working because firewall is blocking.
Disable the firewall of the mac?

---

