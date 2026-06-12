---
title: "gnome do crashes 3s after start up"
date: 2009-02-08
forum: General Help
---

### Post by ptn on 2009-02-08
I used my laptop (with Ubuntu Intrepid) for a few hours today and Do was fine, but when I turned it on again some time later, Do would crash some 3secs after starting. I ran gnome-do in a terminal and I got the attached traceback (do.traceback.txt).  Something to do with an unhandled XML exception.

Odd thing is I didn't change anything in Do's configuration. The only thing I tweaked was something in gstreamer-properties, but I'm pretty sure that has nothing to do here.  I don't think the Skype not running warning has anything to do, either.

I have also included the output of 'mono --debug /usr/lib/gnome-do/Do.exe' (do.monodebug).

I've noticed that I get a different traceback every time I run Do after a restart. I got a very different one this time, something with a 'taskseries'. I attached that too (do.traceback2).

I tried removing with synaptic and then installing back again, but that didn't work.

Any ideas?  If you need some more info, just tell me what to run.


Thanks a lot

P.S  Link to bug report: [https://bugs.launchpad.net/do/+bug/326394](https://bugs.launchpad.net/do/+bug/326394)

---

### Post by skaiuoquer on 2010-04-25
Check [https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/555137](https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/555137) out. This looks like what's happening to you.

---

