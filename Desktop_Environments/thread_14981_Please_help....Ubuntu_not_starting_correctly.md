---
title: "Please help....Ubuntu not starting correctly"
date: 2005-02-11
forum: Desktop Environments
---

### Post by marcadams on 2005-02-11
Hello...

I am having a serious problem - when Ubuntu loads, I :
- hear start up music as the desktop initialises
- the screen cursor
- and what looks like a 1x1 white pixel in the top left of my screen
- and...everything else is black.

(It was previously working fine - until last night)

Luckily the power button on my machine initiates a shut down, otherwise I would have to just turn off the power!


This happened for the first time last night. This morning I started my PC to check, and everything worked fine...On re-boot and subsequent re-boots,  I get the same problem....

A starting question would be - how can I force Ubuntu to perform a file system check (in case I have corrupted files)?

I would be very grateful if anybody could make any suggestions. As soon as I can burn my pesonal stuff onto a DVD, I'll reformat and reload Ubuntu..just in case.


Thanks for your help,
Marc

---

### Post by cblack on 2005-02-11
```
shutdown -r -F now
``` 

That will force a fsck on boot.

Assuming you have ssh installed I'd try to ssh in from another machine and see if your XF86Config file got mucked up somehow. 

Have you tried switching over to a console? Were you able to see anything that way?

---

### Post by marcadams on 2005-02-13
An update, in case this sheds some light on my problem?

I have reformatted and installed Ubuntu, but I still get the same problem.
It seems, if I start my PC from a hard boot then Ubuntu initialises correctly.

However, if I perform a reboot - then I get the a black screen after the boot text has finished (I.e. the desktop it not shown) but I can hear the logon sounds. NB I have autolog on.

Does any body have any suggestions, or are there any log files which I could present to the forum, which could help explore the problem?


Many thanks
Marc

---

### Post by piedamaro on 2005-02-13
Weird, it seems that your monitor frequencies are screwed up in some way upon reboot. Can you try to see if the problem persists after turning autologin off?

---

