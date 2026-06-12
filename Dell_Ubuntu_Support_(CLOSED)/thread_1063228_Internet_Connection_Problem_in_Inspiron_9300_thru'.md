---
title: "Internet Connection Problem in Inspiron 9300 thru' Belkin wired Router"
date: 2009-02-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anncrystal on 2009-02-07
Hi All:
I am a Linux newbie. I installed Ubuntu 8.1 on Dell Inspiron 9300 laptop. However, I couldn't connect to the internet. I'm connecting thru' Belkin Wired Router # F5D5231 (access: 192.168.2.1). Could anybody please help me with setting up (Comcast) internet connection. It may be a piece of cake for you guys.
Thanks in advance
Ann

---

### Post by ugm6hr on 2009-02-07
Please supply more detail.

Is your router already set up?

Does your computer connect to the setup page of the router ([192.168.2.1]("http://192.168.2.1"))?

Does it connect to [208.67.219.101]("http://208.67.219.101")

Or [www.opendns.com/]("http://www.opendns.com/")

Is it on the network?

```
ifconfig
```

If not, what card does it have?
```
lshw -class network
```

---

