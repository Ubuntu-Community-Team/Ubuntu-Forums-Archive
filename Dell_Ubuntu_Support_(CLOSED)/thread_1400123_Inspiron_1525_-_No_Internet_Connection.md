---
title: "Inspiron 1525 - No Internet Connection"
date: 2010-02-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by btthead on 2010-02-06
I have no connection or wireless drivers (I don't think)
When I check like it tells you to in the help and support, it tells me that I should install the Ndiswrapper / ndisgtk thingy.
I did that and I got the driver from windows, but when I installed the driver with ndiskgtk it told me it wasn't the correct driver or something like that. Basically it didn't work

It is definatly the correct driver as I did it twice, one straight from windows and one downloaded from the Dell website.

Please help, nothing too technical, I'm new to this >_<

---

### Post by mikewhatever on 2010-02-06
Ndiswrapper is probably not needed if you are on the latest version of Ubuntu or the previous one. There are native linux drivers for Broadcom, the wireless Dell likes to put in its laptops.
What version of Ubuntu have you installed?
What's the model of your wireless card?

In case you don't know, post the outputs of the following:

cat /etc/lsb-release

sudo lshw -C network

---

### Post by btthead on 2010-02-07
I have 9.10 installed, it worked fine on 9.04

I did the sudo lshw -C network
and the output was huge and it was "Unclamied"

I think my wireless card is 1395 WLAN Mini-Card
yes it's by Broadcom

---

### Post by Zerocool Djx on 2010-02-07
Broadcom drivers need to be downloaded separately. You NEED to plug directly into the internet Via ethernet. Its a conflict of interest for Broadcom to release (for free) there drivers to the open source community because of there contract with Dell (who has contracts with Microsoft). Just go to a friends house and plug in Via Ethernet if you don't have it yourself, takes 5 min and it does it almost automatically after you tell it to download. The drivers in the "Live" test version where only ment for demo use only.

System>Admin>Hardware Drivers>NTS

As far as any manual downloads, it is possible, but chances are you could get in your car and actually drive to your friends house plug it in Download it and come back WAY before you could figure it out, if you don't know Linux. Go do that and learn once you got it working. other wise your going to pull hair out of your head! LOL... 

Trust,,.. I'm doing you a favor by telling you this... but in any event.. yes Ubuntu is a pretty sweet system and if all you got to do is burn 5 bucks in gas to get it working fully, that seems like a steal to me :)

---

### Post by mikewhatever on 2010-02-08
Check out the post below, the model it a bit different, but I think the same driver should work.
[http://ubuntuforums.org/showpost.php?p=8090292&postcount=1](http://ubuntuforums.org/showpost.php?p=8090292&postcount=1)

---

### Post by btthead on 2010-02-15
tried, it didn't pick up any ethernet connection either

---

### Post by btthead on 2010-02-15
X_X
tried it, got up the point where I needed to install, and it would tell me to insert the already inserted disk X_x

---

