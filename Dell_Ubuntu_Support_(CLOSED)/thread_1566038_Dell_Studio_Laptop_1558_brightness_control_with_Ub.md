---
title: "Dell Studio Laptop 1558 brightness control with Ubuntu 10.04"
date: 2010-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gugumatz on 2010-09-01
So I recieved my new laptop studio 1558. I installed Ubuntu 10.04 and found that the brightness control keys didn't work, absolutely nothing happened when I used them.

Then I upgraded my BIOS to version A09. I tried the brightness control keys again and now I was able to see on the screen the brightness scale going up and down, but no actual change on screen's brightness happened... so, help please!

---

### Post by Twintop on 2010-09-11
I'm having a similar problem with my new 1558 as well, only I'm running the 10.10 beta.

Some digging found this bug report on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611)

It looks like there is a confirmed fix, but it isn't in the mainstream kernel yet. :-|

**EDIT:** I just changed how my function keys work (from the BIOS, per this thread: [http://ubuntuforums.org/showthread.php?t=1184539](http://ubuntuforums.org/showthread.php?t=1184539) ) and I'm able to control brightness and whatnot now.

---

