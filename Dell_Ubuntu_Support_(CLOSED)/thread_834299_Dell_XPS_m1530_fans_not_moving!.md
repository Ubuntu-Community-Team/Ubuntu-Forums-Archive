---
title: "Dell XPS m1530 fans not moving!"
date: 2008-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Clockswork on 2008-06-19
So the title pretty much says it all, my fans are not moving even though the CPU temps are above 50 degrees!

What can I do to fix this?

---

### Post by damis648 on 2008-06-19
My fans move, although i think the breaking point is above 50 degrees.

EDIT: My fans just started up. I cannot check the CPU temp, but I can say my ACPI temp was 53 and my GPU core was 62.

---

### Post by Clockswork on 2008-06-19
> **damis648 said:**
> My fans move, although i think the breaking point is above 50 degrees.

EDIT: My fans just started up. I cannot check the CPU temp, but I can say my ACPI temp was 53 and my GPU core was 62.

Have you done anything to get this to work or did it work out of the box?

---

### Post by damis648 on 2008-06-19
Nope, this worked out of the box...

Are you using 8.04 Hardy 32 bit?

---

### Post by Clockswork on 2008-06-19
> **damis648 said:**
> Nope, this worked out of the box...

Are you using 8.04 Hardy 32 bit?

I know it is Hardy 8.04, no idea if it is 32 bit though!

Edit: Ubuntu 8.04 i386

---

### Post by damis648 on 2008-06-19
Post the output of
```
uname -a
```
from terminal.

EDIT: ah, ok Nevermind you have 32-bit. Interesting your fans are not working OTB... how warm is your computer?

---

### Post by Clockswork on 2008-06-19
The outcome of that is
```
Linux clockswork-platform 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

```

the GPU go up to 60C and the CPU to 50C without the fans even moving

I guess I'll re-install :/

---

### Post by damis648 on 2008-06-19
Well don't do that just yet... do something CPU and GPU intensive and see if the fans move... do you have the Compiz running? Spin the cube around and around and around. See if they start up.

---

### Post by damis648 on 2008-06-19
Ah, try what is says in this thread:
[http://ohioloco.ubuntuforums.org/showthread.php?t=772553](http://ohioloco.ubuntuforums.org/showthread.php?t=772553)
I am doing the same, for I just realized the overheat module was not loaded. :-?:-?:-?

---

### Post by damis648 on 2008-06-19
Hm... i cannot manually control the fans but they are still moving automatically... your success?

---

### Post by Clockswork on 2008-10-20
My fans are working now (I went back to Vista a couple moths ago and then re-installed Ubuntu 8.04 last week). They work out off the box with the thresholds of 55C-45C. 

Thought this was abit hot so I searched for another solution and found out that their had been some new BIOS realesed. This lowered the thresholds to 50C-37C.
To lower the CPU idle temp even more (to 40C) I undervolted it abit and now my laptop is cool and lovely :)

Here is a HOWTO i wrote on how to upgrade your BIOS in ubuntu:
[http://www.clockswork.org/?p=3](http://www.clockswork.org/?p=3)

---

