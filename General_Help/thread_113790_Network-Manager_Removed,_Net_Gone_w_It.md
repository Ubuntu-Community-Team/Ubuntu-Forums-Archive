---
title: "Network-Manager Removed, Net Gone w/ It"
date: 2006-01-07
forum: General Help
---

### Post by hopspitfire on 2006-01-07
I installed Network-Manager hoping to have better control over my wlan, and removed it shortly after only to find at my dismay that my internet has been rendered useless (both eth0 and wlan0). When I removed Network-Manager, did it "take" anything with it that is vital to the internet working? If not, what else could be the problem? The internet has not been working since the program has been removed. Thanks in advance for you replies.

---

### Post by bonzodog on 2006-01-07
have you tried starting your net connection from the terminal?
Removing network manager would just have removed any graphical way of controlling the network. Open a terminal, and try:
```

ifconfig eth0 up

```

---

### Post by hopspitfire on 2006-01-07
Hrmm, I tried that, same result. Network-Admin doesn't seem to do anything... i messed around with different settings in there to no avail. Not quite sure what else to do besides nuking the net :P

---

