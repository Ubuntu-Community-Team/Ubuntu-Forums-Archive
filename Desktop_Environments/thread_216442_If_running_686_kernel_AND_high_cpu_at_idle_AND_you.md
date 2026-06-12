---
title: "If running 686 kernel AND high cpu at idle AND you have only one CPU, this might help"
date: 2006-07-15
forum: Desktop Environments
---

### Post by cptnapalm on 2006-07-15
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570)

I was experiencing high CPU usage while idle on my laptop.  Random things would spike the CPU from its low power mode to full power, like moving a mouse.  While digging around for an answer, I came to the above link.

This is ONLY for *single* processor computers with a 686 kernel which experiences high CPU utilization while idle.  Just like the title says :)
Directions:

cd /etc
sudo vi rc.local
and add:  echo 1 > /sys/module/processor/parameters/max_cstate

Now idle CPU is much lower and it throttles down much more quickly.  Things are not vastly faster, but typing, for instance, feels much more snappy, closer to instantaneous.

What the above does is to tell the kernel that there is only one processor.  The high idle is, apparently, due to the multiprocessor core which is the default kernel, thinking that there are multilple CPUs.  By telling it that there is only one, it doesn't erroneously think that.

---

### Post by vinayasurya on 2006-07-15
I think this will be useful to me. Will try

---

