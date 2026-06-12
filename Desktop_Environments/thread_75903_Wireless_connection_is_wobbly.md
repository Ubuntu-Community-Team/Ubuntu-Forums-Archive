---
title: "Wireless connection is wobbly"
date: 2005-10-14
forum: Desktop Environments
---

### Post by geokker on 2005-10-14
Since installing 5.10, I keep losing my wifi connection. It'll only be for a few seconds at a time, but it's enough to knock me out of any SSH sessions, chat etc. I didn't have (much of) a problem with 5.04. How do I troubleshoot this?

---

### Post by dbott67 on 2005-10-14
Could you please post the output of the following commands:

```
cat /etc/network/interfaces
```
```
ifconfig -a
```
```
iwconfig
```
```
iwconfig wlan0 scanning
```

-Dave

---

