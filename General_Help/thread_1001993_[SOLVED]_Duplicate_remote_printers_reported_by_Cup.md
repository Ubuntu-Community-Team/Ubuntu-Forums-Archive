---
title: "[SOLVED] Duplicate remote printers reported by Cups"
date: 2008-12-04
forum: General Help
---

### Post by eurgain on 2008-12-04
Hi

I have three printers on my network: one is directly connected (using hplip) and the others are one USB and one parallel connected to a common host (called Fuchsia with IP 192.168.0.109).  These two printers are shared by cups.

The other machines all use these printers.  On this machine, if I do lpstat -a I get:

eurgain@juno:~$ lpstat -a
HPLaserJet2100M accepting requests since Thu 04 Dec 2008 08:39:33 GMT
Photosmart_8700 accepting requests since Thu 04 Dec 2008 19:55:09 GMT
Stylus-DX7400 accepting requests since Thu 04 Dec 2008 19:42:38 GMT

and this is what I expect, and is the same as I get on my other machines... except one.  On this rogue machine, I get:

eurgain@titus:~$ lpstat -a
HPLaserJet2100M accepting requests since Thu 04 Dec 2008 16:35:58 GMT
HPLaserJet2100M@192.168.0.109 accepting requests since Thu 04 Dec 2008 19:34:06 GMT
Photosmart_8700 accepting requests since Thu 04 Dec 2008 20:05:16 GMT
Stylus-DX7400 accepting requests since Thu 04 Dec 2008 16:35:58 GMT
Stylus-DX7400@192.168.0.109 accepting requests since Thu 04 Dec 2008 19:33:51 GMT

The printers that include the @192.168.0.109 work as expected.  Those without seem to just send their output to /dev/null .  This is extremely invonvenient.  The LaserJet is the default workhorse, and all its output from titus is being dumped.

The files under /etc/cups are identical on all machines.

Does anyone have any idea what is going on?

Thanks
A

---

### Post by eurgain on 2008-12-10
I finally found the answer in Debian bug 504086.

The solution is to remove the /var/cache/cups directory and restart the cups server.

A

---

