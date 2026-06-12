---
title: "Several games fail to load"
date: 2009-05-28
forum: General Help
---

### Post by scorchgeek on 2009-05-28
I recently installed two new games, "BZFlag" and "Battle for Wesnoth." At the beginning, BZFlag worked just fine. When I installed the second one, neither of them, nor some of the default Ubuntu games, work at all. Nothing happens when you attempt to start. If I start from the terminal, I get an error like this:
```
~$ bzflag
Could not initialize SDL Video subsystem: No available video device.
```

Like I said, before everything was working just fine. I have tried uninstalling and reinstalling the second game (to reconfigure it). The only hint I could find was that I also installed SDL-1.2.13 at the same time (since I was trying to compile the second game at first, then realized it was already in the universe repository). I also did a distribution upgrade (silly me installing several things at once). 

My NVIDIA driver is 180.44. It seems to be working just fine. Any ideas?

---

### Post by scorchgeek on 2009-05-31
Seems like I may be stuck running this under Windows :(.

Does anyone think it might help if I reinstalled my video driver?

---

### Post by sti11_learning on 2009-05-31
I have never encountered this error myself. However this forum post may help you. It looks like sdl is the problem. [http://bzbb.bzflag.org/bb/viewtopic.php?t=11670&view=next&sid=501756483d21e05a5c07efef825c5cb3]("http://bzbb.bzflag.org/bb/viewtopic.php?t=11670&view=next&sid=501756483d21e05a5c07efef825c5cb3")

---

### Post by scorchgeek on 2009-05-31
Sounds helpful, but the link is broken. Could you try that again?

---

### Post by sti11_learning on 2009-05-31
Sorry about that. Now try it.

---

### Post by scorchgeek on 2009-06-18
Sorry about the delay. That just didn't work. I think it's a problem with the video drivers, not SDL like the forum thread seemed to indicate at the end.

---

### Post by scorchgeek on 2009-06-18
I posted about this problem on the Wesnoth forums:
[http://www.wesnoth.org/forum/viewtopic.php?f=4&t=25903&p=362636#p362636](http://www.wesnoth.org/forum/viewtopic.php?f=4&t=25903&p=362636#p362636)

If you don't feel like reading it, someone suggested that I probably compiled SDL without X server support. How would I go about doing it with support, if that's indeed the problem?

Thanks for all the help so far.

---

