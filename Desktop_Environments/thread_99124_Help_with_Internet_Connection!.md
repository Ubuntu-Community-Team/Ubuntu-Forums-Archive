---
title: "Help with Internet Connection!"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Georgie-o on 2005-12-05
I have been using Ubuntu on my PC with no internet problems.  Today I changed Routers (purchased a new one) and poof, no more internet.  Can someone tell me how to auto-detect or set up my new router (it's wired).  Thanks.

---

### Post by Qrk on 2005-12-05
I've never tried this with a router, but this might work.

```
sudo dhclient eth0
```

If it doesn't work, you can post the output to help diagnose the problem.

---

### Post by Georgie-o on 2005-12-05
It did not work.  It printed out a bunch of text, but unfortunately I can paste it here as I'm on my Windows Machine (because the other one can't connect to the internet)  anything else I can try or look for?


Thanks

---

### Post by Georgie-o on 2005-12-05
I figured it out!  The computer was not "seeing" the router automatically.  When I disconnected the router and plugged directly into the cable modem it worked immediately.  I used my windows machine to log on to the new router, enterd the I.P address and the Gateway and put it on DHCP and it worked.  This is a big accomplishment for someone who just started learning about networking and did not know you could dial-in to a router until this past week.  Thanks for the help.

---

