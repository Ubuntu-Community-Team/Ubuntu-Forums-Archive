---
title: "Networking Disabled Dell D430"
date: 2010-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TechieJustin on 2010-06-25
Hi folks, I have a Dell D430 here with Lucid 10.04 64 bit.
I put the machine into Hibernate - but it refused to wake up.  Hit a bunch of keys, moved the trackpad and buttons - nothing.
I ended up holding down the power button until it shut down.  When I powered back on networking was disabled.
I went into Hardware Drivers and made sure the proprietary drivers for the wireless were selected.
However, I did a ifconfig and this is what I got:
```
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39600 (39.6 KB)  TX bytes:39600 (39.6 KB)

```

It appears even the ethernet was blown away.  :confused:
So, how toasted am I?

---

