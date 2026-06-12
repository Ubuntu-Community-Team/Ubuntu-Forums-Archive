---
title: "Wireless problem"
date: 2006-08-18
forum: Desktop Environments
---

### Post by silwerspawn on 2006-08-18
I have a Broadcom BCM4306 it is there and  ubuntu says its working, but it aint. it works from my windows partition.
how can i install this wireless lan card?

---

### Post by dpike619 on 2006-08-18
There is a pretty good guide on setting up these types of cards [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper").  I have a 4306 too and it worked for me.

---

### Post by bensexson on 2006-08-18
You will want to decide whether you want to use ndiswrapper or bcm43xx.  If ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) make sure you read the second link first.  If bcm43xx: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper) make sure you read this one first.  I use ndiswrapper because bcm43xx with my bcm4306 won't do 54 Mbps.

---

