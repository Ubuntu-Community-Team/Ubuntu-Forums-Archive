---
title: "Open Ports Puzzle"
date: 2015-05-25
forum: Desktop Environments
---

### Post by Geoff_Lane on 2015-05-25
I have a home network running an Ubuntu Laptop as my main machine and 4 Raspberry Pi devices as well as two PVRs.

The read out of a port scan on network tools is puzzling me. I have one Pi running TVHeadend, the web interface uses port 9981 and the streaming uses port 9982, both work fine and are accessible.

If I use network tools OR nmap via command line it only shows port 22 as open.

I know I am using both programs correctly as one of my Pi devices runs a few servers and all show up.

It is not a maximum range as my server machine shows port 10000 (webmin) which is higher than the TV Headend port.

Any ideas folks?

Geffers

---

### Post by Geoff_Lane on 2015-05-25
> **Geoff_Lane said:**
> 

I know I am using both programs correctly as one of my Pi devices runs a few servers and all show up.

It is not a maximum range as my server machine shows port 10000 (webmin) which is higher than the TV Headend port.

Any ideas folks?

Geffers

Now I am baffled, just run nmap and specified ports 1-10000 and the TV Headend ports (9981 & 9982) showed up fine but port 10000 originally showed up without stipulating ports.

Could it be to do with the /etc/services file?

Geffers

---

