---
title: "Dell mini 1012 can see wireless networks but can't connect"
date: 2010-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dilodicus on 2010-07-16
Running ubuntu 10.04 on a Dell mini 1012, everything was working fine until after getting it back from Dell to have the hard drive replaced (over 150 bad sectors and barely 2 weeks old!!)
 
got the machine back and set up dual boot win7 and ubuntu lucid as before, installed wireless drivers and now the network utility can SEE the SSIDs of nearby networks, but when you try to connect it will try and establish a connection then fail.
 
I have successfully connected to the same networks using Windows 7 on this machine so I must conclude that something in a recent ubuntu update is stopping me from connecting.
 
I have tried both the b43-fwcutter driver (this did not work) and the broadcom STA driver, this gives me SSIDs but won't connect. 
 
It seems lots of people are having problems with dell machines with this broadcom chipset, I'm starting to think maybe I should just buy a replacement wifi card... any suggestions on chipsets that works well with ubuntu?

---

### Post by snowpine on 2010-07-16
It's a bug; see this link for instructions to get your wifi working:

[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

---

### Post by dilodicus on 2010-07-16
Thank you so much!

all working fine now! :)

I was beginning to despair at the thought of having to use windows on this machine!!!!

---

### Post by Thorger on 2010-08-24
> **snowpine said:**
> It's a bug; see this link for instructions to get your wifi working:

[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

no wired connection available...

---

### Post by dilodicus on 2010-09-13
Are you using lucid? if you have another machine I'd suggest downloading a beta iso of maverick... I found lucid became a tad unstable on the dell 1012, but for the last month or so maverick has been perfectly stable :)

---

### Post by dwalkercouk on 2012-06-07
In case anyone else is having the issue with a MIFI device - sees the SSID looks like its connecting but the icon just keeps spinning....  (so never completes the handshake)

Rest assured the fix above worked on 10.04 for our Dell mini 1012.

Also, using this driver other wireless connections are better too, prior to changing it used to drop the wireless connection quite often for no reason even when it was only a few feet away from the wireless router.

---

