---
title: "Computer Half As Fast As It Should Be"
date: 2011-05-12
forum: Desktop Environments
---

### Post by redbikemaster on 2011-05-12
OK, this is something I haven't heard of. I login to my Ubuntu 11.04 and after a while it starts to bog down. It's not extremely fast, but at a processor speed of 2.2Ghz and with 2 GB of RAM it shouldn't be sluggish.

I opened Terminal, ran 'top', and got this:
```

Tasks: 197 total,  12 running, 184 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.3%us, 97.4%sy,  0.3%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2060468k total,  1036576k used,  1023892k free,    98288k buffers
Swap:  2095100k total,        0k used,  2095100k free,   453112k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3242 -username-  20   0 12908 1724 1660 R 23.2  0.1   0:03.70 pagein             
 3187 -username-  20   0 12908 1728 1660 R 22.8  0.1   0:14.93 pagein             
 2385 -username-  20   0 12908 1728 1660 R  6.3  0.1   0:40.38 pagein             
 2403 -username-  20   0 12908 1728 1660 R  6.3  0.1   0:37.46 pagein             
 2446 -username-  20   0 12908 1728 1660 R  6.3  0.1   0:32.05 pagein             
 2460 -username-  20   0 12908 1728 1660 R  6.3  0.1   0:29.11 pagein             
 2332 -username-  20   0 12908 1688 1624 R  6.0  0.1   0:50.09 pagein             
 2422 -username-  20   0 12908 1728 1660 R  6.0  0.1   0:35.79 pagein             
 2474 -username-  20   0 12908 1728 1660 R  6.0  0.1   0:28.45 pagein             
 2487 -username-  20   0 12908 1728 1660 R  6.0  0.1   0:28.02 pagein             
 1976 -username-   9 -11  157m 4936 3568 S  1.7  0.2   0:10.10 pulseaudio         
 3093 -username-  20   0  246m  53m  20m S  1.7  2.7   0:46.61 chrome             
 2631 root      20   0 45656  26m 8088 S  0.7  1.3   0:29.33 Xorg               
 2358 -username-  39  19 39356  23m 3408 R  0.3  1.2   0:00.74 apt-check          
 3207 -username-  20   0  177m  39m  20m S  0.3  1.9   0:03.08 compiz             
 3244 -username-  20   0 92880  13m  10m S  0.3  0.7   0:00.47 gnome-terminal     
 3302 -username-  20   0  2628 1152  840 R  0.3  0.1   0:00.05 top    

```
Please help! This is the third problem in half a week that I've had with 11.04! If this keeps up, I'll have no choice but to install Windows XP! I don't want to do that!!!

---

### Post by sanderd17 on 2011-05-12
> **redbikemaster said:**
> OK, this is something I haven't heard of. I login to my Ubuntu 11.04 and after a while it starts to bog down. It's not extremely fast, but at a processor speed of 2.2Ghz and with 2 GB of RAM it shouldn't be sluggish

Please help! This is the third problem in half a week that I've had with 11.04! If this keeps up, I'll have no choice but to install Windows XP! I don't want to do that!!!


What's that "pagein" command? kan you do
```

killall pagein

```
and see what happens?

Memory and swap seem ok, but the CPU is used too much by that weird command.

---

### Post by redbikemaster on 2011-05-12
Those commands won't die! I tried it before I posted, but they just won't die.

---

### Post by sanderd17 on 2011-05-12
> **redbikemaster said:**
> Those commands won't die! I tried it before I posted, but they just won't die.


I don't know it then, seriously, even google doesn't know about that thread.

---

### Post by redbikemaster on 2011-05-12
Thanks for your input, though.

---

### Post by zealibib slaughter on 2011-05-12
I found this [http://osdir.com/ml/ubuntu-bugs/2011-04/msg46097.html](http://osdir.com/ml/ubuntu-bugs/2011-04/msg46097.html) hope it helps some.

---

### Post by redbikemaster on 2011-05-12
I started it back up today (I shut it off at night for noise reasons) and it wasn't doing it today. Just yesterday.

---

### Post by redbikemaster on 2011-05-30
Quick update: I haven't had this exact problem again.

---

### Post by redbikemaster on 2011-06-02
Still no pagein problem, though I would like to know what that was.

---

