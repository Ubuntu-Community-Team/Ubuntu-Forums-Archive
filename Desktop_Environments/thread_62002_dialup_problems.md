---
title: "dialup problems"
date: 2005-09-03
forum: Desktop Environments
---

### Post by GOwin on 2005-09-03
I've used pppconfig and wvdial (and gnomeppp) but i have no sucess trying to log into my isp using a blank password.

gnomeppp rejects blank passwords outright. using pppconfig, i can't input a blank password. same with attempts to edit the wvdial configuration file.

i'm billed by my ISP based on caller ID, hence the blank password.

thanks.

---

### Post by GOwin on 2005-09-04
bump

---

### Post by az on 2005-09-04
sudo gedit /etc/ppp/peers/provider (or whatever you called it) and try removing the username by hand.  See if that works.

---

### Post by GOwin on 2005-09-04
will try that. thanks

---

### Post by GOwin on 2005-09-06
i find out while reading man chat that "\r" will work for blank passwords in pppconfig.

However, I still have problems. Here's what I get from plog
```
Sep  6 18:47:48 kulaspiro pppd[8724]: using channel 8
Sep  6 18:47:48 kulaspiro pppd[8724]: Using interface ppp0
Sep  6 18:47:48 kulaspiro pppd[8724]: Connect: ppp0 <--> /dev/ttyS3
Sep  6 18:47:49 kulaspiro pppd[8724]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x236c937d> <pcomp> <accomp>]
Sep  6 18:48:19 kulaspiro pppd[8724]: LCP: timeout sending Config-Requests
Sep  6 18:48:19 kulaspiro pppd[8724]: Connection terminated.
Sep  6 18:48:19 kulaspiro pppd[8724]: Receive serial link is not 8-bit clean:
Sep  6 18:48:19 kulaspiro pppd[8724]: Problem: all had bit 7 set to 0
Sep  6 18:48:20 kulaspiro pppd[8724]: Exit.
```

---

### Post by GOwin on 2005-09-07
*bump*

---

