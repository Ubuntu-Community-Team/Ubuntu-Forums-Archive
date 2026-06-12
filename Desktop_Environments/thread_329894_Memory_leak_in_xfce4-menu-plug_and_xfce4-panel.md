---
title: "Memory leak in xfce4-menu-plug and xfce4-panel?"
date: 2007-01-02
forum: Desktop Environments
---

### Post by trippyd on 2007-01-02
I am using XUbuntu Edgy,  I have googled around and haven't found a good answer for this one, so I thought I would try here.

The system:
Dell Optiplex, 3gig HT CPU
1 Gig ram.

Basically, from a restart (of the computer or X), xfce4-menu-plug and xfce4-panel will start out taking around 1% of the system memory each.  As time passes, whether I am doing anything or not, this number will slowly grow.  

For example, I have been away from my work PC for 3 days with the new years holiday/weekend, and when I arrived this morning, each process was taking 12-13% of my system memory.  I figured out that these two guys were the culprits one time when they were each taking 25% of my system memory (half of my system memory between them).  It doesn't seem to be related to what I have open or what I am doing, the number just slowly grows.

This isn't an end of the world kind of problem, I just have to restart X to get them down to a more respectable level, but it is pretty annoying.

Any thoughts?

Thanks,
D

---

### Post by Jiawen on 2007-08-10
This is pretty much [this bug]("https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/77702"). 

This is a huge problem for me. I end up having to restart Xfce every couple days because the swap usage grows and grows. Restarting means I have to laboriously slog through quitting every program. Grr! Someone please fix this bug!

---

