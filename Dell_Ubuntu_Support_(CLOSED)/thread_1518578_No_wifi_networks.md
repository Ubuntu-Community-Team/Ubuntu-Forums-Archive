---
title: "No wifi networks"
date: 2010-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by slimtonio on 2010-06-26
hi,

I have just installed Ubuntu 10.04 on my dell inspiron 13z (after having totally format the HD, and reinstall windows 7 first, with the CD Dell gave me).
But it seems like ubuntu does not recognize any wifi networks !! 
the ethernet connection works fine, but it does not recognize any wifi networks.
any idea how to solve that please???

thank you!

---

### Post by teejaybee on 2010-06-26
Does "ifconfig" list your wifi device? wlan0? Does dmesg/syslog show your wireless device as being detected? Have you tried configuring any wireless networks in the network manager?

---

### Post by slimtonio on 2010-06-26
sorry i am a begginer i don't know how to do all that, can you explain me please?

---

### Post by slimtonio on 2010-06-26
just a precision: it works well on windows 7

---

### Post by slimtonio on 2010-06-26
Ok I found it.
Actually the drivers were not installed, so I just had to do it.
Sorry...
It now works very well.
If some other beginners have the same problem the solution is just to install the drivers (in System ->Administration)

---

### Post by teejaybee on 2010-06-26
I've found a nice guide that will help you step by step.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

To execute some of the commands they need you to use (like ifconfig as I said above) you open a terminal by clicking Applications > Accessories > Terminal and run them there.

Let us know if you have any problems.

---

### Post by teejaybee on 2010-06-26
No worries - good luck with it all.

Be sure to keep your system up-to-date using System > Administration > Update Manager and use WPA2 security on your wireless AP with a strong passphrase if possible.

---

### Post by gopa on 2010-07-23
Hi, I was planning to buy this dell inspiron 13z model to install Ubuntu 10.04.
Since you already done so, could you tell me your experience of Ubuntu on Inspiron 13z
Did u ever experience any problem with the graphics (is it NVIDIA that you have)
any help and suggestion regarding a good hardware configuration of this model will
be useful for me.

expecting your useful suggestions :)

---

