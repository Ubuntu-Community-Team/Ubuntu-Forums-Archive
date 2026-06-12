---
title: "can't get wireless to work"
date: 2009-04-02
forum: General Help
---

### Post by saskatchewan on 2009-04-02
I am running a compaq presario with an AMD 64 processor and I have a 
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

But, I can not get the wireless to work.  I have been looking around the site but none of the instructions have worked'

i.e. [http://ubuntuforums.org/showthread.php?t=760568&highlight=Dell+WLAN+1390](http://ubuntuforums.org/showthread.php?t=760568&highlight=Dell+WLAN+1390)

Suggestions please...........

---

### Post by ptn107 on 2009-04-02
I have a compaq v2000z laptop from 2005 with the exact same integrated network adapter.  The soultion is in System -> Administration -> Hardware Drivers and enabling the proprietary drivers for it (or just installing b43-fwcutter_[1:011-4ubuntu1]**).

**direct links:
hardy: [http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_amd64.deb)
intrepid: [http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-4ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-4ubuntu1_amd64.deb)
jaunty: [http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-5_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-5_amd64.deb)

---

### Post by saskatchewan on 2009-04-02
When I go to those sites there is just gibberish and I can't read it.

I am running Firefox 2

---

### Post by saskatchewan on 2009-04-03
When ever I  click on the box to enable those drivers it says that there has to be firmware downloaded to make it work.  I click OK and the box has an x for a few seconds and then it vanishes.

Then nothing really changes.  There is still no wireless....

Help!!

---

