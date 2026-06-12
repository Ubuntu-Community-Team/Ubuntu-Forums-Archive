---
title: "problems with flash player 10"
date: 2009-01-30
forum: Desktop Environments
---

### Post by the_overmind on 2009-01-30
ok so Im running Ubuntu 8.10 and I just had a huge system crash. I was running kernel update and forgot it was going and put my laptop into suspend of course the system wont start up again restarted it a few times nothing. so then of course I reinstall Ubuntu but I did not use an 8.10 disk I used an 8.04 disk while updating to 8.10 I installed adobe flash player 10 and here's where all hell breaks loose I go on Youtube it works fine at first go to a video link the browser crashes I retried this like 5 times and nothing I reinstalled flash player 10 like 6 times and still nothing is there any way I can delete flash player 10 and downgrade to flash player 9?
FIXED, THANKS BRANIMIR

---

### Post by Branimir on 2009-01-30
did you install it through package manager or manually?
With package manager you simply deinstall. But I don;t 
know how to bring earlier version.

If manually there is directory /usr/lib/mozilla/plugins
where all so files reside.
So you can mv somewhere else libflashplayer.so version 10
and put version 9.

Strange 64 bit version of libflashplayer.so works perfectly
to me. Even I can scroll fields with mouse that I could'nt
do before with 32 bit version.

Greetsa, Branimir.

---

### Post by the_overmind on 2009-01-30
perfect took you advice i just uninsulated it from synaptic package manager and reinstalled flashplugin-nonfree. Thanks:D

---

