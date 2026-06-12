---
title: "Problems running Istanbul in Edgy"
date: 2006-09-15
forum: Desktop Environments
---

### Post by th3t1nm4n on 2006-09-15
I was wondering if anybody had been successful at running Istanbul in Edgy, all my packages are up to date, I installed Istanbul, and I get this:
```
tinman@Debaser:~$ istanbul
Traceback (most recent call last):
  File "/usr/bin/istanbul", line 30, in ?
    from istanbul.main import main
  File "/usr/lib/python2.4/site-packages/istanbul/main/main.py", line 25, in ?
  File "/usr/lib/python2.4/site-packages/PIL/__init__.py", line 21, in ?
    
ImportError: No module named ltihooks
tinman@Debaser:~$ 

```

Google brings this up: [https://launchpad.net/distros/ubuntu/+source/istanbul/+bug/31960](https://launchpad.net/distros/ubuntu/+source/istanbul/+bug/31960)
But that doesn't help me much at all.

Thanks in Advance
--TinMan

---

### Post by Brightrock on 2006-12-06
It will run on my computer but there is clearly a problem.  The video freaks out and the audio is pretty good.  I'm running it in gnome.  I tried it first with beryl and xgl running it looked about the same.  Any help would be appreciated.  

BR

---

