---
title: "Firefox consuming more resources the longer it is running"
date: 2008-12-19
forum: General Help
---

### Post by ag65151 on 2008-12-19
I have noticed that if I leave Firefox (3.0.4) running all the time it consumes more and more of my system resources.

When I look at the output of "top" in a terminal, the "%wa" number is in the 90's. I am certain this means that 90% of the active processes are waiting on I/O action. And my hard disk light being constantly on seems to confirm the same. When I exit Firefox, it takes a while, but the %wa numbers decline back to less than 10%.

Has anyone else experienced anything like this?

(Ubuntu 8.10; HP ZE5500 laptop; P4M - 2.6Ghz; 256MB; ATI IGP 340M video card)

---

### Post by RealPSL on 2008-12-20
Can you provide the output of the following when Firefox is running with the problem and when it is not?

```

free -m
ps aux | grep firefox

```

---

### Post by ag65151 on 2008-12-20
I just restarted the machine for other reasons, so here is the output without the problem.

```

~$ free -m
             total       used       free     shared    buffers     cached
Mem:           438        428          9          0          5        140
-/+ buffers/cache:        282        155
Swap:         2117          7       2110
~$ ps aux|grep firefox
me    8092 29.5 20.3 225600 91348 ?        Sl   11:48   1:05 /usr/lib/firefox-3.0.4/firefox
me    8287  0.0  0.1   3236   804 pts/0    S+   11:52   0:00 grep firefox

```

---

### Post by RealPSL on 2008-12-21
I guess we have to wait until you have the problem. Based on the output you sent Firefox is using using 20% of RAM and you have 155 of RAM that can be used for either file caching or applications. Firefox generally grows in size and all indications are this is because of the plugins. Send the output when the problem is happening as well. 

You can try disabling some plugins selectively by using firefox flashblock for example.

[http://flashblock.mozdev.org/]("http://flashblock.mozdev.org/")

---

### Post by ag65151 on 2008-12-22
Yes, we have to wait, but I am having the problem now. Here are the results of the above requested commands.

```

myuser@myuser-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           438        430          7          0          0         30
-/+ buffers/cache:        399         38
Swap:         2117        630       1487
myuser@myuser-laptop:~$ ps aux|grep firefox
myuser    8092  4.2 61.1 601212 274360 ?       Rl   Dec20 133:58 /usr/lib/firefox-3.0.4/firefox
myuser   15666  0.0  0.1   3236   804 pts/0    S+   15:46   0:00 grep firefox

```

---

