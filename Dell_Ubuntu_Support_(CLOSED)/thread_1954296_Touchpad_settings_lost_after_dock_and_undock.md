---
title: "Touchpad settings lost after dock and undock?"
date: 2012-04-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by T3kG33k on 2012-04-07
I've been having a strange issue since I've began using Ubuntu on my Dell Latitude D630 and 610.  The touchpad settings are apparently lost upon docking.  If I restart, shutdown, or sleep the system then the settings are back to normal.  The same thing happens after undocking.

This has been occuring since using Ubuntu 9.x and I'm currently using 10.10.  I would be using 12.x but it ran like crap on my D630 :cry:

I read that if I run ```
sudo modprobe -r psmouse; sleep 5; sudo modprobe psmouse
``` That the issue should be resolved but I have no clue as to create a udev rule.

This isn't a major problem but more of an annoyance that has persisted for a long time.

---

### Post by T3kG33k on 2012-04-10
No one?

---

### Post by cortman on 2012-04-10
I'm having the same problem with my Acer Aspire One netbook. I plan to write a small script with some synclient commands, and have it run at startup. Assuming you have synaptics installed, open a terminal and run

```
synclient
```

You'll get a long list of possible commands and values (some boolean) for each. You can set different features on and off by typing 

```
synclient VertEdgeScroll=1 
```

as an example. This would turn on vertical edge scrolling.

---

