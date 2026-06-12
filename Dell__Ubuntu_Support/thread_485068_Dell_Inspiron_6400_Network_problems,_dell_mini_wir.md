---
title: "Dell Inspiron 6400 Network problems, dell mini wireless"
date: 2007-06-26
forum: Dell  Ubuntu Support
---

### Post by AllanJP on 2007-06-26
Hey everyone!

First, I've seen some of the post on this toppic, but still I'm confused. My problem is souly that my network card wount work!? my laptop specifications are:

Inspiron 6400 Dual-Core Processor T2060(1.6GHz/533MHz/1MB)
15.4" Wide Screen WXGA (1280 x 800) TFT Display
512MB 533MHz DDR2 SDRAM (1x512)
60GB (5,400 rpm) Hard Drive
Intel Media Accelerator 950 Graphics Up to 256MB shared graphics memory
Dell Wireless 1390 802.11b/g 54Mbps Mini-PCI Wireless Card, for Dual Core Processors

I've hard something about restricted drivers needed to be downloaded. Is this true, and if is, where/how to get them.

I've seen tutorials on how to use ndiswrapper, and also heard that this is not stabil in the long run... 
Are there really nothing else to do when you own an Inspiron 6400 with this kind of networkcard? 
I really whant to use my Ubuntu on my laptop, I hope you can show me in the right direction.

In advance Thanks

---

### Post by walkerk on 2007-06-26
Uh.. you need ndiswrapper. It is very stable. I have a 6400 and the same wireless nic. Just follow one of these threads (the gtk installer might be the easiest.. not sure as I used the command line)

[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom")
[http://ubuntuforums.org/showthread.php?t=457371&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=457371&highlight=broadcom")
[http://ubuntuforums.org/showthread.php?t=297092&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=297092&highlight=broadcom")

---

### Post by AllanJP on 2007-07-25
Ok! thanks.. I tried the one with the gtk installer and it worked like a charm... It took what? 5 min. and then it was up and running.. 

THANKS !!

---

### Post by softone4u2 on 2007-09-21
Hi 

Can you please post the steps followed because I have the same wireless card and havent been able to make the wireless running...

I am using ubuntu 6.06 desktop version ....

I have ndiswrapper on the desktop ...and bcmdrivers too 

I have blacklisted bcm43xx 

And one more problem I encountered is when I plug in network cable for Lan it is still showing the loopback so kindly advice how to make wireless running as well as the broadcam lan if possible....

I will be really thankful...


Sam...

---

