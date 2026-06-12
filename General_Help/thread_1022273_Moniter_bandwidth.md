---
title: "Moniter bandwidth?"
date: 2008-12-26
forum: General Help
---

### Post by Monotoko on 2008-12-26
Is there anything i can use to moniter the bandwidth i use? and kill my net it if it reaches a certain point

---

### Post by AlexBellisBrown on 2008-12-26
In system montior, it tells you how much youve downloaded/uploaded in that session. But to kill the wireless i imagine you would need some kind of script. *Bump* Anyone any ideas?

---

### Post by fragos on 2008-12-26
Here's a script I run at the end of the day that both displays bandwidth useage for the and records it in a log file. It doesn't do any comparisons but it does keep me up on what I'm using. 

#!/bin/bash
date >> /home/fragos/Desktop/bandwidth.log
ifconfig eth1 |grep bytes
ifconfig eth1 |grep bytes >> /home/fragos/Desktop/bandwidth.log

---

