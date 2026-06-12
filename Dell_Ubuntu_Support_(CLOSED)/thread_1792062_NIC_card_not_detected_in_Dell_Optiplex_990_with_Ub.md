---
title: "NIC card not detected in Dell Optiplex 990 with Ubuntu 10.04"
date: 2011-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sramanujam on 2011-06-27
I had recently purchased a Dell Optiplex 990 desktop system in which I tried installing Ubuntu 10.04 LTS OS. The OS installation was successful, however, after restart, I found that Ubuntu is not able to detect the NIC card. The status of the network connection icon shows a warning sign with red exclamation mark. When I click on it, it says "No available connections found". However, the ethernet cable is working fine which I checked by connecting the same to my laptop, and my network connection is up and running.

Further, the "Wired" tab under "Network connections" window is not showing "Auto eth0". Could this be an issue with the driver? I checked with Dell website for support, but to my disappointment, I found that they are providing support for NIC driver only for Windows operating systems. Looking forward to get community support from Ubuntu for getting the network connection established in my new pc.

Thanks

---

### Post by mörgæs on 2011-06-29
Do you get wired internet access when booting a live 10.10 or 11.04?

---

### Post by sramanujam on 2011-06-30
Lucid is not able to detect the NIC. I think the driver for latest hardware is not bundled with the live cd. I installed Natty which has detected the NIC and got connected to the internet.

---

### Post by mörgæs on 2011-06-30
Good, then please mark the thread 'solved'.

---

### Post by sbq on 2012-01-06
In my case, I have to run 10.04 64-bit because other software I'm using requires it.  The solution to this unrecognized ethernet controller is documented here:  [http://fosiao.com/node/18](http://fosiao.com/node/18).  It's easy.  You have to cd into the src/ directory before running "make install".

---

