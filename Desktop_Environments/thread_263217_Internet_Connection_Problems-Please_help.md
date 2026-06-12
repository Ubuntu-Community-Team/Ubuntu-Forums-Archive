---
title: "Internet Connection Problems-Please help"
date: 2006-09-22
forum: Desktop Environments
---

### Post by jimminy_kriket on 2006-09-22
I use a dsl connection with username/password. Ive set it up using sudo pppoeconf but that only worked the very first time I used it. I cannot get it to work at startup, the only way I can get it to work is by rerunning sudo pppoeconf, then disabling and re-enabling my ethernet adapter in the network settings panel. But even that rarely works and I have to try over and over before I get lucky and it works. 

Running plog shows me this when its not working:

Sep 22 16:47:55 jamie-desktop pppd[9194]: Plugin rp-pppoe.so loaded.
Sep 22 16:47:55 jamie-desktop pppd[9196]: pppd 2.4.4b1 started by jamie, uid 1000
Sep 22 16:47:55 jamie-desktop pppd[9196]: PPP session is 3014
Sep 22 16:47:55 jamie-desktop pppd[9196]: Using interface ppp1
Sep 22 16:47:55 jamie-desktop pppd[9196]: Connect: ppp1 <--> eth0
Sep 22 16:47:55 jamie-desktop pppd[9196]: PAP authentication failed
Sep 22 16:48:01 jamie-desktop pppd[9196]: Connection terminated.
Sep 22 16:48:01 jamie-desktop pppd[9196]: Modem hangup

And this when it is working:

Sep 22 16:48:29 jamie-desktop pppd[9223]: Plugin rp-pppoe.so loaded.
Sep 22 16:48:29 jamie-desktop pppd[9225]: pppd 2.4.4b1 started by jamie, uid 1000
Sep 22 16:48:29 jamie-desktop pppd[9225]: PPP session is 3015
Sep 22 16:48:29 jamie-desktop pppd[9225]: Using interface ppp1
Sep 22 16:48:29 jamie-desktop pppd[9225]: Connect: ppp1 <--> eth0
Sep 22 16:48:29 jamie-desktop pppd[9225]: PAP authentication failed
Sep 22 16:48:31 jamie-desktop pppd[9196]: PPP session is 3016
Sep 22 16:48:31 jamie-desktop pppd[9196]: Using interface ppp2
Sep 22 16:48:31 jamie-desktop pppd[9196]: Connect: ppp2 <--> eth0
Sep 22 16:48:32 jamie-desktop pppd[9196]: PAP authentication failed

If anyone can help, please do!

---

### Post by sharkcohen on 2006-09-22
Not sure if you want the expense, but I would suggest getting a cheap cable/dsl router and having it handle PPPoe.

---

