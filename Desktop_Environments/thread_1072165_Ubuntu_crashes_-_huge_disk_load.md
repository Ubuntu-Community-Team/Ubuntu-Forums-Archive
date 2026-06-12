---
title: "Ubuntu crashes - huge disk load"
date: 2009-02-17
forum: Desktop Environments
---

### Post by szymex on 2009-02-17
I have Ubuntu 8.10 and sometimes it crashes, so even mouse does not work. It seems that disk usage is very high. What could be a reason of that? How can I check the reason? 

Szymon

---

### Post by prshah on 2009-02-17
> **szymex said:**
> It seems that disk usage is very high. What could be a reason of that? How can I check the reason? 

You could have:

a) Low free memory / no swap memory. Check the output of ```
free -m 
``` for this; if the output is not clear to you, post it here for an explanation. If you have 256Mb or less or RAM, it is very likely this is your problem.

== OR ==

b) a physically / logically damaged hdd. A quick check is to see if the following command gives any output; if it does, then post back the output for a resolution. If there is no output, this is (probably) not a HDD problem.```
 dmesg | grep -i drdy\|emask
```

---

### Post by szymex on 2009-02-17
First case: it is unlikely that it would be lack of memory becase this computer has 2GB of ram although I couldn't run freem command, how to install it?

The second case: I didn't get any output.

---

### Post by prshah on 2009-02-17
> **szymex said:**
> I couldn't run freem command

Sorry that's a misspelling; it's supposed to be "free". However, since you say you have 2 Gb RAM, this point is moot. You can ignore this now.

Many have complained that wineserver sometimes causes a lot of disk thrashing, and firefox as well at times. Maybe you should look for threads related to this on the forums. 

Here's something to start you off:
[Hardy Hanging Daily with Excessive Disk I/O]("http://ubuntuforums.org/showthread.php?t=810595")

---

### Post by szymex on 2009-03-19
I'm still having that problem. Now I know that it happens because firefox uses a lot of memory. In system monitor sometimes I saw that firefox was using more than 800MB and couple of minutes later huge disk load started, computer was not responding.
Any ideas how to prevent that disk load due to memory leaks from firefox?

Szymon

---

### Post by linux_tech on 2009-03-19
Have you tried limiting memory in firefox?
[http://kb.mozillazine.org/Memory_Leak](http://kb.mozillazine.org/Memory_Leak)

---

