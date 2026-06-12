---
title: "Inspiron 8100"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by E1Designs on 2007-09-01
First issue is random stuttering where the system locks up for a split second or so, then returns to normal. Saw a post with no response regarding this same behavior and it was mentioned that something to do with power may exist.

Second, wireless woes. DWL-650+ card, HW:BB1 FW:1.9...now it was auto-detected, installed, is able to see wireless networks, so it is operating, the issue lies in trying to connect to a wireless network, with or without WEP, no luck. I would prefer to not use ndiswrapper, help out if you can.


Thanks In Advance

---

### Post by E1Designs on 2007-09-01
u-bump-tu

---

### Post by foolios on 2007-09-02
I am having a problem finding linux drivers for my DLink DWL-650. 

Where did you find drivers for yours? The D-Link site shows that they don't have linux support for this wireless card. 

Thanks in advance for the heads up.

---

### Post by E1Designs on 2007-09-02
They  are not from D-Link, which means they are a 3rd party driver if you will -- loaded during the Ubuntu install, when detecting devices inserted in to the PCMCIA slot.

In regards to the power problem...[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/24353](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/24353)

I am somewhat closer on that...

---

### Post by Staceman on 2007-12-07
Did you ever find a solution to this problem?

I ask, because I just got done getting settled into my new Gutsy install on this Inspiron 8100, and was searching around the 'net for information about the same problem. Same thing I did about, oh, 2 years ago, same distro. I hoped that it would have been fixed by now, but it's probably a rather obscure problem; I was lucky to find more hits in my search this time, I wasn't so lucky the last time.

Anyway, I found a post somewhere that mentioned turning off/disabling a service called "powernowd", fixes the problem. I did so about 15 minutes ago, and can verify that this does indeed fix the problem.

The downside is that if you run your Inspiron 8100 on battery power often, you will lose the CPU throttling feature, which helps in prolonging your battery use. If you're like me, though, and have a battery that lasts about 5 minutes unplugged, and don't feel that the laptop is worth getting a new battery for, or you don't use it in situations where you would need to use the battery, you won't miss it. ;-)

---

### Post by cstronach on 2007-12-09
Check this fix out:

[http://ubuntuforums.org/showthread.php?t=75598&highlight=powernowd](http://ubuntuforums.org/showthread.php?t=75598&highlight=powernowd)

---

