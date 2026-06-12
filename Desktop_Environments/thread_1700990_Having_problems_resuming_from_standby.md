---
title: "Having problems resuming from standby"
date: 2011-03-05
forum: Desktop Environments
---

### Post by Ali.A on 2011-03-05
[SIZE=2]i am running Ubuntu 10.10 i386 on my computer

and i put my computer to standby[/SIZE] [SIZE=2]

but when i tried resuming i couldn't [/SIZE] [SIZE=2]

i pressed EVERYTHING on my keyboard and i still couldn't resume so i  eventually had to shutdown the computer and start it up again[/SIZE] [SIZE=2]

so... can anyone help me to solve this resuming problem[/SIZE]

---

### Post by jeremyjjbrown on 2011-03-05
Do you have a /swap partition on your HD?

---

### Post by Copper Bezel on 2011-03-05
Let's make this the real thread. It looks like it was double-posted.

Swap wouldn't matter for suspend, would it? I guess it's possible that he or she really means hibernation.

In any case, the problem (and fix) are likely to be hardware specific, so what's your make and model number?

---

### Post by pastalavista on 2011-03-05
My problem was the same until I found a post saying to install the 'hibernate' package and reboot.. which didn't work at first, until the latest kernel update ( 2.6.35-28 )
```
sudo apt-get install hibernate
sudo apt-get update
sudo apt-get upgrade
```
I would have thought 'hibernate' would have been installed by default, but it wasn't.

---

### Post by jeremyjjbrown on 2011-03-05
> **Copper Bezel said:**
> Swap wouldn't matter for suspend, would it?

No it wouldn't, but Standby is what they said. They didn't say whether this meant suspend to memory or "hibernate" suspend to disk.

---

