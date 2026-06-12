---
title: "Problem with alsa and cedega... but ONLY cedega"
date: 2005-05-13
forum: Gaming &amp; Leisure
---

### Post by Chareos on 2005-05-13
Hi everybody,


I'm almost TOTALLY satisfied Ubuntu64 user on amd64 platform.


My pc is based on a nforce4 chipsed which worked out of the box (amazing!)

As of now I'm facing a problem with cedega and alsa.
Before, I must say that killing esd I'm able to get sound from xmms using alsa, so all's fine.
Also, I can get it working even as a user, so no permission problems.

Coming to cedega, using alsa it don't works. I tried to configure it to "hw:0,0" (that is good as I can see in xmms) with no success.


Note: I've to use alsa with cedega: using oss sound is stuttering and makes loud static noises. And, above all, alsagives lower latency and better performances.



Anybody can help me to make cedega working with alsa ?


Many thanks.

---

### Post by Chareos on 2005-05-13
Tried a little more...
it WORKS fine with oss if I kill powernowd (I found I can functionally restart it by the name).

so Alsa is not a problem.


Now... seems a little unstable... argh. I'll try deeper.

---

### Post by DutchLau on 2005-05-13
I've read something about this before, Cedega (although I don't use it myself)  doesn't seem to be compatible with ALSA. Just run it with OSS.

Good Luck,

DutchLau

---

### Post by Chareos on 2005-05-13
When I was on slackware (32 bit of course) I used ALSA. Maybe the problem is related to Ubuntu too... or maybe to the Ubuntu kernel. Next days I'll try a personal kernel.


Oh, another question... looking forward for powernowd down/up automation, is there a way to instruct sudo to let a user execute powernowd without bothering for password ?
Let's say, a way to give a specific user the power to launch powernowd (and only powernowd) AS root and without password request ?

And, if I would like to do the same for esd ? killing it before and then restart after finish, which command should I issue to get it started again ? "esd" only don't seems to give back gnome the voice...

---

