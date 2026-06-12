---
title: "Does not pull IP at boot"
date: 2005-11-09
forum: Desktop Environments
---

### Post by DrBair on 2005-11-09
My machine hangs at boot at 'configuring network interfaces'.  I added in some extra logging to my init script and confirmed that it gets stuck when doing 'ifup -a'.  

daemon.log on the machine claims that dhclient was started and polled for an IP but recieved no offers.  I also had tcpdump running on my server machine and it never sees the requests.  

After the machine is booted I can do an 'ifdown eth0', 'ifup eth0' and then I can see the request on my server which then quickly responds with a reply and then everyone is happy again. 

Any ideas? My network card is an intel e1000 and I'm using the latest and greatest 686-smp kernel from the repositories.  

Thanks!

---

### Post by DrBair on 2005-11-09
FIXED!

Turns out the e1000 needs to be explicitly brought up _before_ running dhclient.  Right now I just glued 'ifconfig eth0 up'  in the init script and it works great.  

This should really be added to the distro as it seems to be common to e1000's.  

Any ideas on how I can make this less of a hack? Seems like that if-pre-up.d folder could be useful...

---

