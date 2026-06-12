---
title: "E1505N - slow wifi speed?"
date: 2007-06-13
forum: Dell  Ubuntu Support
---

### Post by Chasoid on 2007-06-13
I just got my E1505N and I'm very happy with it.

One problem/question... the wifi network speed appears to be much slower than the other laptops in my household that also have 802.11g wifi.

For example, my wife's laptop can download from my local FTP server at around 10MBps.  This new laptop only downloads via FTP at around 3MBps.

Any thoughts as to why this new E1505N laptop would be so much slower?  I've benchmarked their FTP speeds several times, always with the same results.  (Yes, they both are connecting to the same rounter and trying to download the same file.  I'm using ncftp as the FTP client).

Using scp produces similar, slower results for this new laptop.

Any thoughts on what I should adjust or look at to speed up the network speed?

Thanks much.

---

### Post by mojorising on 2007-06-14
Some thoughts:

Are you using the same FTP client on both PCs? Same OS setup, etc?

Have you tried plugging in with a cable to see if it produces different results?

Maybe also try a different live CD like Knoppix to see what performance is like there.


Mike

---

### Post by Chasoid on 2007-06-14
I should have mentioned that, yes, I did use exactly the same setup.  Both used Ubuntu 7.04 and ncftp.

Thanks.

---

### Post by AJL on 2007-06-14
Could this be a firmware VS ndiswrapper situation?

I mean, maybe you aren't really connecting via 802.11g?

```

IEEE WLAN Standard 	Over-the-Air (OTA) Estimates  	Media Access Control Layer, Service Access Point (MAC SAP) Estimates
802.11b 	11 Mbps 	5 Mbps
802.11g 	54 Mbps 	25 Mbps (when .11b is not present)
802.11a 	54 Mbps 	25 Mbps

```

---

### Post by tgalati4 on 2007-06-14
It's possible that you have a bad wireless chip.  With cost-cutting, the quality of construction becomes a factor in overall laptop performance.  It's possible that the wireless chip has problems at the higher speeds and defaults to a slower speed.

Sounds like you need to get into the internals of the wireless and start comparing data between the two laptops.

What is the signal-to-noise between the two systems?

sudo ifconfig
sudo iwconfig eth0 (where eth0 is the device from ifconfig)
sudo iwlist eth0 scan
sudo iwpriv eth0 [feature you are interested in--see man iwpriv]

Let us know what you find.  My guess is an antenna connection problem--something physical and not software related.  Could be as simple as a pinched antenna wire in the case.

---

### Post by mojorising on 2007-06-14
Kinda grasping a straws a bit here but are they in the same room? Does performance improve if you move the laptop right next to the AP? 

Mike

---

### Post by Chasoid on 2007-06-20
*** RESOLVED ***

Yes... I'm an idiot!  <blush!> :oops:

My "other" laptop was also configured the same and using wifi ... blah ... blah ... blah.

BUT... it was ALSO plugged into a 100mbps ethernet cable.  And that's why it was getting a much faster transfer rate.

As another post in this thread pointed out (THANKS, by the way!) 802.11g gives you about 25Mbps over the air.  Figuring that you lose about 1/8 (or 12.5%) of that due to TCP overhead, allowing that FTP has almost no overhead on its own, and then doing the 8 bits per byte calculation, you get:

25 * 7 / 8 / 8 = 2.73 MBps.  Which is about what I got.

Thanks for the replies.  It's working perfectly.  :D

Loving Ubuntu on my E1505N,
Charlie Brune
St. Louis, MO.

---

