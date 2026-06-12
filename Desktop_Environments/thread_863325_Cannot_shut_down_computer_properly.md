---
title: "Cannot shut down computer properly"
date: 2008-07-18
forum: Desktop Environments
---

### Post by Paul Chang on 2008-07-18
I cannot properly shut down both my desktop and laptop. I am running Ubuntu 6.04 on my desktop (self-built), and 8.04 on laptop (Dell 700m). When I tried to shut down the machines, once in a while (not always), the screen seems to be turned off, but the hard drive light is still on, and I can still hear the noise of the spinning fans until I remove the power cable (and battery for laptop) to fully turn off the machines. This happens for all the Ubuntu distributions since 6.04, even including Linux Mint, a Ubuntu variation. Any gurus have a solution?  Many thanks!

---

### Post by tuxxy on 2008-07-18
If you are trying to shutdown from the menu, then you could try from the terminal;

> sudo shutdown -h now

---

### Post by Paul Chang on 2008-07-19
thanks, tuxxy.

But the problem is I don't know when is the machine not going to be shut down properly.

---

### Post by silkstone on 2008-07-19
The next time you get this problem, after rebooting look at the file /var/log/kern.log

That records all activities during boot-up and shut-down, and also when devices are connected and disconnected. It is possible that you will see from that where the problem occurred. My knowledge is not good enough to tell you how to fix it, but at least you may identify the cause.

---

### Post by warp99 on 2008-07-19
It could be a module that needs to be unloaded before shutdown, most likely the sound module. You could try this:

```
echo "rmmod snd-hda-intel" |sudo tee -a /etc/default/halt
```

I believe that's the correct module for you Dell Inspiron 700m.

---

### Post by Paul Chang on 2008-07-21
someone suggest put "acpi=force apm=power_off" in menu.lst. Since my problem occurred randomly, I really don't know if this really works for my case.

---

